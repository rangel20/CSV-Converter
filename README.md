# Challenge Requirements

## CSV Converter

You work on a system that processes registrations for a national event. People register through a web page. At the end of the registration period, data from all registrants is compiled into CSV (Comma-Separated Values) files.

There is a subsystem responsible for post-processing the registrations that supports CSV files. However, the formatting of the information that this subsystem expects to receive is different from the formatting of the files generated by the web page.

**Your goal is to develop a Java program capable of converting the files generated by the web page to the format required by the subsystem.**

## Description of input and output files

The CSV files generated by the web page are available in the `inputs` folder, separated by state. For example: `sp.csv`, `mg.csv`, `ba.csv` (not limited to these three!). For each file contained in the `inputs` folder, you must create a corresponding file with the same name in the `outputs` folder.

The input files can be treated as text files and have the following standard structure:

- The first line is always a fixed header that contains the column names separated by commas:
```text
Full name,Date of birth,Email,CPF
```

- Each of the following lines contains a registrant's information, also separated by a comma. Example:
```text
Moacir Monforte,04/07/1986,monforte@yahoo.com,72614377279
```

The following conditions are guaranteed regarding the input files:

- All birth dates are in Brazilian format: `dd/mm/yyyy`
- All emails are valid
- All CPFs (Brazilian individual taxpayer registry) are valid and composed of exactly 11 decimal digits (without dots or hyphens)

The full names of the registrants may be in uppercase, lowercase or mixed case.

The required formatting for the output files is as follows:
- The header must be the same as that of the input files.
- The full names of the registrants must be standardized in all uppercase letters (graphic accents should be maintained).
- Birth dates must be in ISO-8601 format: `yyyy-mm-dd`.
- CPF numbers must be correctly formatted with a dot and hyphen. Example: `123.456.789-09`.

Lines in output files must be arranged in the same order as those in input files.

## Exemple

For the following input file: `inputs/sp.csv`
```text
Full name,Date of burth,Email,CPF
IRANI TAPEREBÁ,29/06/2001,tapereba@gmail.com,81627775471
catarina mafra,28/05/1991,cmafra@gmail.com,75157671466
bento naves,25/12/1993,b.naves@aol.com,88826690685
Lurdes Neves,08/04/1985,lurdes.neves85@verizon.net,92277079138
```

The following output file must be produced: `saidas/sp.csv`
```text
Full name,Date of burth,Email,CPF
IRANI TAPEREBÁ,2001-06-29,tapereba@gmail.com,816.277.754-71
CATARINA MAFRA,1991-05-28,cmafra@gmail.com,751.576.714-66
BENTO NAVES,1993-12-25,b.naves@aol.com,888.266.906-85
LURDES NEVES,1985-04-08,lurdes.neves85@verizon.net,922.770.791-38
```

## Code requirements

Your code should be built from the `Converter` class below:

```java
import java.io.File;
import java.io.IOException;

public class Converter {

  public static void main(String[] args) throws IOException {
    File inputsFolder = new File("./entradas/");
    File outputsFolder = new File("./saidas/");
    new Converter().convertFolder(inputsFolder, outputsFolder);
  }

  public void convertFolder(File inputsFolder, File outputsFolder) throws IOException {
    // TODO: implement.
  }
}
```

You can add as many methods and auxiliary attributes to the `Converter` class as you like, as long as the class name and `convertFolder` method signature are preserved.

For this challenge, you don't need to worry about handling exceptions (they will be seen in the next section 😉). When writing certain helper methods, you may need to add `throws IOException` to their signature to avoid compilation errors.

Now it's up to you! The registration system is in your hands, so focus on the quality of the result, agreed? #VQV 🚀