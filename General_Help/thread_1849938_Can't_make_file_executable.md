---
title: "Can't make file executable"
date: 2011-09-25
forum: General Help
---

### Post by kecal.op on 2011-09-25
I can't make file executable. When I try to change it through the right click/properities/permissions/allow executing file as program, it seems it's ok for a while and after a approximately a second, the box is empty again. When I try it through terminal, at won't give me any error, but the file still isn't executable.
I try to use google, but I can't find any way to solve this problem.
Thank you for your time and sorry for my english.

---

### Post by lordbux on 2011-09-25
> **kecal.op said:**
> I can't make file executable. When I try to change it through the right click/properities/permissions/allow executing file as program, it seems it's ok for a while and after a approximately a second, the box is empty again. When I try it through terminal, at won't give me any error, but the file still isn't executable.
I try to use google, but I can't find any way to solve this problem.
Thank you for your time and sorry for my english.

When i had the same problem i first changed the ownership and then tried.
```
 sudo chown $USER <file path>
sudo +x <filepath>
```

should do the trick. ):P

---

### Post by raja.genupula on 2011-09-25
Hi 
   No need to change user to make file as execute. 
   Just do this 

   ```
sudo chmod +x filename
```

all the best

---

### Post by Morbius1 on 2011-09-25
I don't use Wubi but are you trying to make a file on the host ( i.e., Windows ) directory executable?

That's not going to work. You can't chmod or chown a Windows file as they have no Linux permission bits to change.

If you're trying to change it to executable so something runs in Wine then you're in luck: [http://ubuntuforums.org/showthread.php?t=1747138](http://ubuntuforums.org/showthread.php?t=1747138)

---

### Post by kecal.op on 2011-09-25
I try to do what you say and still it saying it's not marked as executable.
I write this
```
sudo chown tlauli /media/Data/Download/Minecraft/minecraft.jar

```
(I have similar problem before, too, it's not fault of minecraft)
write password a then try to change the executability by
```
sudo chmod +x /media/Data/Download/Minecraft/minecraft.jar
```And still nothing. :-\ The case of letters is correct.

EDIT: raja.genupula: Like I wrote in my first post, that comand does nothing.
      Morbius1:In windows that file is an "executable jar file". And if I understand correctly to link that you posted, they try to solve a problem with opening the file with wine. But I don't want to open it with wine, just normaly with sun java or opemJDK java.

---

### Post by Morbius1 on 2011-09-25
Same problem with a jar, same culprit ( cautious-launcher ), same solution:

**Change the file association:**
Right click an *.jar file and select Properties  -> Open With -> Add -> Use a custom command > type in:
```
java -jar 
```
In the "Open With" tab mark the "jar"[COLOR=Black] [COLOR=Blue]**you added**[/COLOR] [/COLOR]as   the default .

---

### Post by bcbc on 2011-09-25
See this howto to mount the partition in a way that makes the file executable: [http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

---

### Post by Morbius1 on 2011-09-25
Crikey, exe's and jar's don't have to be set as executable to run in Linux. It's a file association problem caused by cautious-launcher.

Here, I'll prove it to you. In a terminal run the following command with the jar file that's not executable:

```
 java -jar /media/Data/Download/Minecraft/minecraft.jar
```It may not run because of something wrong with that jar file but you will **not get** an error telling you it's not executable.

---

### Post by pkg9991 on 2011-09-25
i'm facing a similar problem and
sudo chmod +x filename 
is not helping

---

### Post by bcbc on 2011-09-25
> **Morbius1 said:**
> Crikey, exe's and jar's don't have to be set as executable to run in Linux. It's a file association problem caused by cautious-launcher.

Here, I'll prove it to you. In a terminal run the following command with the jar file that's not executable:

```
 java -jar /media/Data/Download/Minecraft/minecraft.jar
```It may not run because of something wrong with that jar file but you will **not get** an error telling you it's not executable.

That may be - but the original post asks how to make a file executable. I think Wormzy's HowTo is a must read for anyone dual booting. 

Either way... it's not worth getting all excited over.

---

### Post by kecal.op on 2011-09-25
> **Morbius1 said:**
> Same problem with a jar, same culprit ( cautious-launcher ), same solution:

**Change the file association:**
Right click an *.jar file and select Properties  -> Open With -> Add -> Use a custom command > type in:
```
java -jar 
```
In the "Open With" tab mark the "jar"[COLOR=Black] [COLOR=Blue]**you added**[/COLOR] [/COLOR]as   the default .

Thank you. It doesn't matter it is marked executable or not, the important part is that I can start it. It give me an error now, but that's a different problem. :-)

Edit:
> **bcbc said:**
> See this howto to mount the partition in a way that makes the file executable: [http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)
This was exactly what I was looking for. Than you for your help.

---

### Post by bane1151 on 2011-09-25
i'm running ubuntu 9.04 or 9.10 and i tried to download and play Minecraft, and it won't work, can anyone help? i did the java -jar and it loaded but when i went to start a world it closed... does anyone know why this happened?

---

### Post by lordbux on 2011-09-26
> **bane1151 said:**
> i'm running ubuntu 9.04 or 9.10 and i tried to download and play Minecraft, and it won't work, can anyone help? i did the java -jar and it loaded but when i went to start a world it closed... does anyone know why this happened?


The reason for the application getting closed may be a bug in the application and not with the way you run it. 

But let's see

Start the application in terminal and wait till it close, now close 
Run the following:

```
script -a -c **"**java -jar <path>**"** ~/Desktop/MClog.log 
```
**the " " (quotes around the command is important**

Now attach that file with your post. ..or paste content in 
Thank you
:popcorn:

---

### Post by Morbius1 on 2011-09-26
> **kecal.op said:**
> Edit:
     
                                                                      Originally Posted by **bcbc**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=11284843#post11284843")                 
                 > *See this howto to mount the partition in a way that makes the file executable: [http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)*This was exactly what I was looking for. Than you for your help.
Just remember that mounting ntfs and fat32 partitions is not like mounting a linux filesystem. You can set them up to make all files non-executable ( the default in Ubuntu ) or all files executable but nothing in between. So unless you go after the file association itself as a remedy you may get your jar and exe's to run but you will set all your *.txt files, Word documents, spreadsheets, mp3's, etc...  marked as executable as well.

---

