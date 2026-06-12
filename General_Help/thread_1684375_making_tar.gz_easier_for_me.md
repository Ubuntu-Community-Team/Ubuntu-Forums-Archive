---
title: "making tar.gz easier for me?"
date: 2011-02-09
forum: General Help
---

### Post by ninjaking92 on 2011-02-09
Ok so I am still new to Linux. I am sick of downloading these Tar.gz files and not being able to do anything with them. I dont know where they are supposed to extract to or anything. I could ask about specific programs but that wont work. I want to know how to instal programs contained in any Tar.gz file. How do these fiels work and what is the easiest way to use them?

I have been all over google and im not finding anything. Everyone has a different way of doing it and im confused and a bit mad. In windows its a simple .exe. Why cant it be this simple in linux?

---

### Post by jordsters on 2011-02-09
Well, programs contained in tar.gz files are mostly things that you can find in the Ubuntu Software Centre (Applications --> Ubuntu Software Centre). Ubuntu is built to only run programs from the Software Centre, but if you're sure that the item contained in the tar.gz file is a program, extract it, right-click it, press "Properties", then "Permissions" and then check "Allow executing file as program". Run it and it should work/install.

---

### Post by vidtek on 2011-02-09
> **ninjaking92 said:**
> Ok so I am still new to Linux. I am sick of downloading these Tar.gz files and not being able to do anything with them. I dont know where they are supposed to extract to or anything. I could ask about specific programs but that wont work. I want to know how to instal programs contained in any Tar.gz file. How do these fiels work and what is the easiest way to use them?

I have been all over google and im not finding anything. Everyone has a different way of doing it and im confused and a bit mad. In windows its a simple .exe. Why cant it be this simple in linux?

Nin-
The tar.gz are compressed files rolled into one, such as the .zip files you are used to with Windows.

There the similarity ends.

Ubuntu has an inbuilt archive manager, and when you examine the archive there will be several subfolders and lots of files inside them.  
As Jordster says, if you can find the programme for which you are searching using synaptic or apt-get from the command-line you are far better off doing so as a newbie.

If the app. you want is only available (or the version you want isn't in the repositories) as a tarball then you will have to do a little (lot)bit of learning to use them correctly.

After extraction, look through the archive until you find a read me file which should have detailed instructions of how to install the programme.

You will need to compile the programme yourself (not as bad as it sounds).  In order to do that your system needs some basic compiling stuff, such as the linux source and/or headers cc+ etc.
There are many places on the net with better guides than I can give in a small reply for compiling programmes on Linux.

You will then enter what is termed "dependency hell".  You will be unable to install this programme because you have't got this one, it goes on and on.....

Take my advice, as a newbie, stick with the repositories and .deb files until you are ready to tackle other stuff and you have a spare week or five.

Tony.

---

### Post by Fxkrait on 2011-02-09
Go to Terminal and change directories to where you downloaded the files, if your using firefox and downloaded something from the internet type cd ~/Downloads. Then type tar xzf file.tar.gz. for file put the name of the file. There will be a new folder in your downloads section that you can now run your application.

---

### Post by mcduck on 2011-02-09
> **ninjaking92 said:**
> Ok so I am still new to Linux. I am sick of downloading these Tar.gz files and not being able to do anything with them. I dont know where they are supposed to extract to or anything. I could ask about specific programs but that wont work. I want to know how to instal programs contained in any Tar.gz file. How do these fiels work and what is the easiest way to use them?

I have been all over google and im not finding anything. Everyone has a different way of doing it and im confused and a bit mad. In windows its a simple .exe. Why cant it be this simple in linux?

It's even sipler in Linux. Use the package management. Or if you have to, download a .deb package, which you'll be able to install simply by clicking on it. Just like the .exe installers on Windows, but with less OK->OK->OK clicking and EULA agreements etc... :D

.tar.gz is just like a .zip file, nothing but an archive that can contain anyhting. And just ike nobody can give you an answer to "how to install any zipped program in Windows?", nobody is going to be able to answer "how to insall any .tar.gzipped program in Linux?". :)

If yu really, really cant find a program you need in the software repositories, or as a .deb package, then pretty much every program distributed as a gzipped package will contain instructions. Read them and you'll nwo if you have to just extract the contents somewhere and run it, or compile it into a program, or something else. If there are no instructions, ask the person who made the program.

---

### Post by ninjaking92 on 2011-02-09
Well I always have the crappy luck of finding a program in Tar.gz and not having it be anywhere else.

---

### Post by Frogs Hair on 2011-02-09
Ubuntu documentation doesn't provide one procedure for installing a .tar.gz . It is suggested that the package be extracted and the instructions if any with the package be followed.

---

### Post by oldos2er on 2011-02-09
[http://amitech.50webs.com/installing/index.php.html](http://amitech.50webs.com/installing/index.php.html)

---

### Post by 3rdalbum on 2011-02-09
> **ninjaking92 said:**
> Well I always have the crappy luck of finding a program in Tar.gz and not having it be anywhere else.

Maybe those programs are not in Software Center for a reason. Usually the programs in Software Center are the most mature, most popular, most useful and most up-to-date. Start your search in Software Center and if you don't find anything useful, THEN look around at the internet for other options.

There's no universal ".tar.gz" installation procedure, because ".tar.gz" is just an archive format, and programs distributed in this manner are usually intended for developers and advanced users to compile and package. They should have instructions, anyway.

If you can, look for "PPAs" or "repositories" that contain the software you want; they tell Software Center about all the software contained in them. Failing that, look for .deb files as they are Ubuntu's native package format.

---

### Post by ninjaking92 on 2011-02-09
Alright. Thanks for the help everyone. I guess I will have to try to figure out how to install these programs some other way.

---

