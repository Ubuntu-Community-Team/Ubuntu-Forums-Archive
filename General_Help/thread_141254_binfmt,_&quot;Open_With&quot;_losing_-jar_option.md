---
title: "binfmt, &quot;Open With&quot; losing -jar option"
date: 2006-03-07
forum: General Help
---

### Post by chub_mackerel on 2006-03-07
Two very related puzzles, regarding Java and jar files.  

I'm trying to set it up so that I can double click a *.jar file, and have it run.  Should be simple.

1) I know that I can go to Properties, Open With... and add a custom command: java -jar.  BUT it simply doesn't work.  It seems to (?) lose the -jar option altogether, just listing "java" in the open with dialog.  Then when I try to run it by double clicking, no response whatsoever.  I've tried with the file set to executable and not, FWIW.  I can run it directly from the command line (java -jar Program.jar), no problems, so I know the jar is built correctly as an executable jar file.

2) In my efforts to work around problem #1 I found out about binfmt, which actually seems like a better way than "Open with..."  But I'm having similar trouble setting that up too (though I'm not sure if it's actually related):  I can't get the "-jar" option into the command.  I'm doing things like 

```
sudo update-binfmts --install javajar "/usr/bin/java -jar" --extension jar
```

But it insists on looking for a program "java -jar" instead of starting up "java" with "-jar" as an option.  I've tried with single, no quotes, etc.  

Any suggestions on getting either/both of these to work?  Thanks in advance for any help.

---

### Post by NeilGreenwood on 2006-03-09
I managed to get the code you posted to work. The key is to create a small shell-script (I called it /usr/local/bin/java-jar) which has the "java -jar" command in it.

```
#!/bin/sh
/usr/bin/java -jar $*

```

Then run ```
sudo update-binfmts --install javajar /usr/local/bin/java-jar --extension jar

```

Make the jar executable, and everything works!

HTH
Neil

---

### Post by chub_mackerel on 2006-03-09
Well, that works for the console (Thanks!).  But double clicking on the icon to start the program still doesn't work for some reason...  

It just opens up the file in my archive manager (since *.jar is a compressed format).  Setting the jar file as executable seems to make no difference at all.  

Note: I also tried making my new batch file (/usr/local/bin/java-jar) into the default "Open With..." application.  That doesn't work either...  If I do that, nothing at all happens when I double click.  

Hrmmm.

:-k

---

