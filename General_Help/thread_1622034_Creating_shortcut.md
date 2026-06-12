---
title: "Creating shortcut"
date: 2010-11-15
forum: General Help
---

### Post by Lucrin on 2010-11-15
ok I want to create a shortcut on my desktop for minecraft (a game). I think I have to create a launcher but I am not really sure what to do because to launch minecraft I have to do it through a terminal command as follows:

navigate to ~/Minecraft
do command "java -jar Minecraft.jar"

So how do I enter all that into a launcher? Thanks.

---

### Post by amauk on 2010-11-15
Right click on desktop > Create launcher

in the command box,
```
java -jar ~/Minecraft/Minecraft.jar
```

---

### Post by DeMus on 2010-11-15
> **Lucrin said:**
> ok I want to create a shortcut on my desktop for minecraft (a game). I think I have to create a launcher but I am not really sure what to do because to launch minecraft I have to do it through a terminal command as follows:

navigate to ~/Minecraft
do command "java -jar Minecraft.jar"

So how do I enter all that into a launcher? Thanks.

Yes, create a launcher. Right-click on an empty part of your desktop and choose: Create launcher.
You get 3 fields which need to be filled:
Name: This will be the name of the launcher, the text you see below the picture.
Command: this will be, in this case: ~/Minecraft/java -jar Minecraft.jar
Comment: any comment you want to write here.

---

### Post by Lucrin on 2010-11-15
@amauk:
I tried your method and when I use the shortcut nothing happens at all. However if I type "java -jar ~/Minecraft/Minecraft.jar" in terminal it loads up fine.

@DeMus:
When I try your method I get the following error when executing the shortcut:
"Details: Failed to execute child process "~/Minecraft/java" (No such file or directory)"

Any other ideas?

---

### Post by amauk on 2010-11-15
> **Lucrin said:**
> @amauk:
I tried your method and when I use the shortcut nothing happens at all. However if I type "java -jar ~/Minecraft/Minecraft.jar" in terminal it loads up fine.
Change the "Type" box from "Application" to "Application in terminal"

---

### Post by Lucrin on 2010-11-15
> **amauk said:**
> Change the "Type" box from "Application" to "Application in terminal"
Already tried that, still does nothing.

---

### Post by amauk on 2010-11-15
Hmmm,
probably a working directory issue

Try this

Make a text file (using gedit), and type in

```
#!/bin/sh

cd ~/Minecraft
java -jar Minecraft.jar
```

save the file in your home directory, say as "run_minecraft.sh"

right click file, and allow "executing as a program"

then create a launcher to the file
- Type: App in terminal
- command: ~/run_minecraft.sh

---

### Post by Lucrin on 2010-11-15
I couldn't put the file in home because when I tried to save it there it said I don't have permission so instead I put it in home/nate.
When I do that a terminal window opens with the following error:
There was an error creating the child process for this terminal
Failed to execute child process "~/nate/run_minecraft.sh" (No such file or directory)

Also note I adjusted "~/run_minecraft.sh" to "~/nate/run_minecraft.sh"

---

### Post by amauk on 2010-11-15
> **Lucrin said:**
> Also note I adjusted "~/run_minecraft.sh" to "~/nate/run_minecraft.sh"Don't :)

take out the "nate", so it just reads
~/run_minecraft.sh

the tilde (~) means your home directory, which is /home/nate

---

### Post by Lucrin on 2010-11-15
Ok I took nate out and it just alters the error a bit:
Failed to execute child process "~/run_minecraft.sh" (No such file or directory)

---

### Post by amauk on 2010-11-15
did you save the script above to a file named "run_minecraft.sh" in your home directory?

---

### Post by Lucrin on 2010-11-15
yep its there along with other things like my documents/picture folders etc

EDIT: So you know if I double click the script and tell it to run it works.

---

### Post by amauk on 2010-11-15
Well, you could just cut & paste the script from your home directory to your desktop....

no idea what's going on with the launcher, though

---

### Post by Lucrin on 2010-11-15
Alright cool, thanks!

---

