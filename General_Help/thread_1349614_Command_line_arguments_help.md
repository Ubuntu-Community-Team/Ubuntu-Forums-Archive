---
title: "Command line arguments help"
date: 2009-12-08
forum: General Help
---

### Post by may22 on 2009-12-08
Hi I am new to java and need help on how to change this bit of code below
 
import java.util.Scanner;
import java.io.File;
import java.io.IOException;
import java.awt.image.BufferedImage;
import javax.imageio.imageIO;
import.java.awt.Color;
public class FinalExam
{
public static void main(String [] args) throws IOException
{
Scanner keyboardInput = new Scanner(System.in);
System.out.print("Input the address of the image (e.g. c:\\myPicture.jpg)");
String imageLocation = keyboardInput.nextLine();
File imageFile = new File(imageLocation);
BufferedImage storedImage = ImagIO.read(imageFile);
}
}
 
does anyone know how I would change this code to supply the the name of and image file as a command line argument when issuing the command to run the program??

---

### Post by Rob_H on 2009-12-08
This isn't really the right forum for Java questions. But for what it's worth, you can get access to command line arguments via the args variable. So you could write something like this:

```

String filename = "";
if (args ! = null && args.length == 1) {
  filename = args[0];
}

```

---

