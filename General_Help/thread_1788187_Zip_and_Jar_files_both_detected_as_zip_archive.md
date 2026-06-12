---
title: "Zip and Jar files both detected as zip archive"
date: 2011-06-22
forum: General Help
---

### Post by kirill578 on 2011-06-22
As you may know JAR file are zip archive, therefor I can't set my Ubuntu to open (by defualt) JAR file with Java and ZIP files with Archive Manger.

---

### Post by mike555 on 2011-06-22
just set the "open with" properties .

---

### Post by kirill578 on 2011-06-22
That is the problem: if I set Java to open jar, Java also open zip but default
basically i can't set  "open with" individually to each one of them

---

### Post by varunendra on 2011-06-23
I don't get it.

If one file has extension name .zip and the other .jar, then their properties will show their file types as "Zip archive" and "Java archive" respectively. On the same property box, if you set a different application on the "Open with" tab for one of the file types, then 'only' that file type will start opening with the changed application while the other one will stick with the default one.

I haven't tried Natty yet but don't think that'll make any difference to this behaviour.

If you are experiencing otherwise, please post screenshots of the property boxes of both the file types - showing "Open with" tab.

---

### Post by Gyokuro on 2011-06-23
Can you try to run the jar file from command line (terminal, gnome-terminal,...) 

java -jar app.jar

---

### Post by derklempner on 2011-06-23
> **kirill578 said:**
> That is the problem: if I set Java to open jar, Java also open zip but default
basically i can't set  "open with" individually to each one of them
**.jar** files are generally used as executable files, to be opened by your Java Runtime program.  If your computer is trying to open them as archives _and_ trying to open **.zip** files when you change the default program, change the default program back for **.zip** files (Archive Manager) and simply change the permissions of any **.jar** file to be executable with the default program to open them as JDK.

---

### Post by kirill578 on 2011-06-23
I think it was somekind of bug, I reinstalled Java and it solved the problem

---

