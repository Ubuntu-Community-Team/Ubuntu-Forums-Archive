---
title: "Create launcher for java file as root"
date: 2010-12-25
forum: General Help
---

### Post by timbalisto on 2010-12-25
I have a java.jar (PCGen) that only works correctly if I run it with sudo from the terminal. I have to cd into its directory and run it as ```
sudo java -jar pcgen.jar
```I would like to use a menu launcher instead of having to use the terminal each time. I tried ```
sudo java -jar /path/to/file/pcgen.jar
``` No luck. This .jar only works properly if ran as root, is there any easy way to do this?

---

### Post by noah++ on 2010-12-25
**gksudo **instead of **sudo**?

---

### Post by timbalisto on 2010-12-25
Uh-oh. It appears I made a mistake in diagnosing my problem. Running it as root doesn't matter, running it from the terminal is what makes it work. If I start it through nautilus or a menu launcher, it doesn't work, but if launched from the terminal it works fine. Is there a solution to my problem?

---

### Post by idi0tf0wl on 2010-12-27
> **noah++ said:**
> **gksudo **instead of **sudo**?
That's just gonna give you a visual prompt for your password rather than a terminal one.

What kind of program is it? Is it a GUI application or what? From the command-line you can make the file executable with:
```
sudo chmod +x /pathto/file.jar
```
or you can right click it in nautilus and navigate to Properties/Permissions and check the "allow executing as program" option. Then you'll be able to right-click the jar file and open it with whatever Java runtime you want. Keep in mind that unless this is a GUI application, you will not see any output running it in this way, and make sure your path doesn't include any unquoted spaces (this might be why you reported having to navigate to the folder before running it effectively).

Cheers!

---

