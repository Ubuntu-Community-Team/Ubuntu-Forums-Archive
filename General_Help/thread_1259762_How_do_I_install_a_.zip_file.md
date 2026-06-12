---
title: "How do I install a .zip file?"
date: 2009-09-06
forum: General Help
---

### Post by harecanada on 2009-09-06
Hi,
How do I install a .zip file? I downloaded something I want to try and it's on my Desktop as a .zip file but I don't know what to do from here.
Anybody around who could help?
Thanks,
harecanada

---

### Post by andrew.46 on 2009-09-06
Hi harecanada,

> **harecanada said:**
> How do I install a .zip file? I downloaded something I want to try and it's on my Desktop as a .zip file but I don't know what to do from here.

Well, a zip file is simply a compressed archive but of course this is more commonly seen on a windows system than a linux system. You will need to give a little more information about what you are trying to accomplish I suspect, such as the name of the application, the actual location of the download and the contents of the zip file. These contents can bee seen from the commandline for example:

```
unzip -l ***[COLOR="Red"]myfile.zip[/COLOR]***
```

All the best,

Andrew

---

### Post by mike555 on 2009-09-06
in most cases you rt. click on it and unzip it ...... you should always install from your package manager if the program you want is there , because that way it will automatically be updated for you ...

---

### Post by credobyte on 2009-09-06
While we are at the level of "something" - you can't install a .zip file. It's an archive!
Unzip it, tell us what you have there & someone might help you a little bit faster ..

---

### Post by harecanada on 2009-09-06
Sorry, I didn't explain this better. 
I went to this site 
[http://mac.wareseeker.com/download/flesh-2.0.rar/334844](http://mac.wareseeker.com/download/flesh-2.0.rar/334844) 
I downloaded Flesh 2.0. It is a document readability calculator. 
There is a Linux version and I downloaded it to my Desktop. The icon is not a file folder. It's a box with this written under it Flesh-Linux.zip

harecanada

---

### Post by cholericfun on 2009-09-06
right click should give you the optionj to "unzip" it
afterwards you probably have just the program there ready for install
see if there are any "readme" files and go from there on

---

### Post by andrew.46 on 2009-09-06
Hi harecanada,

> **harecanada said:**
> I downloaded Flesh 2.0. It is a document readability calculator. There is a Linux version and I downloaded it to my Desktop. The icon is not a file folder. It's a box with this written under it Flesh-Linux.zip

It all becomes a little clearer now :-). There are no installation instructions with this one, simply the file Flesh.jar and README.txt + some Mac instructions. Simply unzip as:

```
unzip Flesh-Linux.zip
```

and you will see the instructions in the README file:

```
Flesh 2.0 Multi-Platform Release

Requires Java 1.5+

Run with:
java -jar Flesh.jar [fileName]
```

Following these instructions the program obligingly popped open a window and I left it at that as I am unfamiliar with this program and its uses, but I have attached a screenshot :-). Is this the program you are after?

Andrew

---

### Post by harecanada on 2009-09-07
Andrew ,
This is the program I'm looking for . How did you get it to open? Did you put the second code in a terminal? What did you put in for the  [filename] ?
harecanada

---

### Post by rockstarrem on 2009-09-07
I don't think you have Java installed. Your going to need to do that first.

[http://www.java.com/en/download/index.jsp](http://www.java.com/en/download/index.jsp)

Tell us if you have problems with that.

---

### Post by QIII on 2009-09-07
Unless the you are fairly familiar with downloading and installing something like Java and absolutely must have Update 16,  I would not recommend going the route of downloading from Sun and attempting the installation as instructed.

Better to go to the terminal

```
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-bin sun-java6-fonts sun-java6-jdk
```

Then, to make sure that Sun Java is used in case OpenJDK is also installed

```
sudo update-java-alternatives -s java-6-sun
```

Finally, to check the version

```
java -version
```

The Universe repository has to be in the Sources list.

The Jaunty repositories have Java Update 14.  But unless you need Update 15 or 16, this should be fine.

---

### Post by andrew.46 on 2009-09-07
Hi harecanada,

> **harecanada said:**
> This is the program I'm looking for . How did you get it to open? Did you put the second code in a terminal? What did you put in for the  [filename] ?

Well to tell the truth the program ignored whatever I put there for *[filename]* obviously expecting some other sort of file :-). But looks like the program gui will open up simply with the following command in a terminal window:

```
java -jar Flesh.jar
```

and then take input from the little Browse button. As long as you are sure that this a reputable program I guess you could put it in /usr/local/bin:

```
sudo cp -v Flesh.jar /usr/local/bin
```

and create an alias for it in ~/.bashrc:

```
alias flesh='java -jar /usr/local/bin/Flesh.jar'
```

and then the program could be started from any terminal window and run simply as:

```
flesh
```

to get the gui running. There would be several different ways of doing this but I would personally do it this way, although I am usually accused of making things too complicated :confused:.

Andrew

---

### Post by rockstarrem on 2009-09-07
Learn something new everyday here :).

---

### Post by harecanada on 2009-09-07
Andrew ,
Thanks very much man. It works perfectly. This program is included in Microsoft Word and is used in Article marketing but it is not used in Open Office yet. I don't have anything to do with Microsoft so had to figure something else out.
Do you know if there is any way to make a launcher for it on the Desktop?
Thanks again,
harecanada

---

### Post by andrew.46 on 2009-09-07
Hi harecanada,

> **harecanada said:**
> Do you know if there is any way to make a launcher for it on the Desktop?

Well to tell the truth on closer examination all my cleverness with aliases did not work all that well on my own system so it is just as well that a launcher on the Desktop worked a little better :-). I have attached a couple of screenshots that show my eventual success! (Right click on your Desktop first and select 'Create Launcher'...) I will slog away on the alias idea where I am obviously missing something important...

Andrew

**Edit:** I have corrected my foolish mistake with the bash alias and it now works fine ....

---

### Post by harecanada on 2009-09-08
Hi Andrew,
I'm doing something wrong. The only way I can get the GUI is to cd to Desktop and then put in  java -jar Flesh.jar in the terminal. Then I get the GUI. I must be putting the wrong Command in the Launcher.
harecanada

---

### Post by andrew.46 on 2009-09-08
Hi harecanada,

> **harecanada said:**
>  I must be putting the wrong Command in the Launcher.

The command in the launcher should be:


```
java -jar /usr/local/bin/Flesh.jar
```

or you can alter the path if you have the Flesh.jar file in a different place...

Andrew

---

### Post by credobyte on 2009-09-09
Move your JAR file to /usr/local/bin and add this line to ~/.bashrc:
```
alias flesh='java -jar /usr/local/bin/Flesh.jar'
```

Now, when you want to use it, type in flesh ( you can create a launcher for it as well ) and you are ready to go :)

---

### Post by harecanada on 2009-09-09
Ok Andrew. That works. Thanks again for all the help and thanks to everyone else for the input.
harecanada

---

### Post by andrew.46 on 2009-09-09
Hi harecanada,

> **harecanada said:**
> Ok Andrew. That works. Thanks again for all the help and thanks to everyone else for the input.

Great news :)

Andrew

---

### Post by lilithdog on 2009-12-10
Hi, I am trying to unload a zip file named:

[ftp://ftp.cbcb.umd.edu/pub/data/bowtie_indexes/s_cerevisiae.ebwt.zip](ftp://ftp.cbcb.umd.edu/pub/data/bowtie_indexes/s_cerevisiae.ebwt.zip)

It keeps saying no such file or directory.  The bowtie file is on the desktop/bowtie-0.11.3

How do i make this work?

---

