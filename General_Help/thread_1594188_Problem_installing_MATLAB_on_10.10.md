---
title: "Problem installing MATLAB on 10.10"
date: 2010-10-12
forum: General Help
---

### Post by 3rd on 2010-10-12
Hello,

I am a complete Ubuntu novice so please be kind!
I have just installed 10.10 (64 bit) and am trying to install MATLAB r2010b.
I execute the MATLAB install file (as root) and I get the following output:

Preparing installation files ...
Installing ...
eval: 1: /tmp/mathworks_15227/java/jre/glnxa64/jre/bin/java: Permission denied

Could anyone advise me why I get this error and how I can make the install work?
Thanks,

3rd

---

### Post by supergrav on 2010-10-12
Hello!
When executing installation file you're using sudo?

---

### Post by 3rd on 2010-10-12
I have tried both sudo and executing the file as root (I activated the root account).
I get the same problem in both cases.

---

### Post by supergrav on 2010-10-12
Do you have java installed?

---

### Post by 3rd on 2010-10-13
I didn't have Java installed, but I have installed it now and it makes no difference.

---

### Post by keerkegan on 2010-10-18
Thats a permision problem, try to change them all to 777 and it will work.

---

### Post by Tandrial on 2010-10-21
okay, I have a similiar problem. Also trying to install Matlab under Ubuntu 10.10. But it doesn't even go as far as the OP posted.

When I try to install  Matlab 2010b with 

sudo sh install

I get this 

dirname: fehlender Operand
„dirname --help“ gibt weitere Informationen.
---------------------------------------------------------------------------
Error: Cannot locate Java Runtime Environment (JRE).
The directory /java/jre/glnx86/jre does not exist.

The weird thing is that that folder exsits in the .iso. So I'm kind of confused on what to do here. Can someone help?

thanks

---

### Post by nej_simon on 2010-10-27
> **Tandrial said:**
> okay, I have a similiar problem. Also trying to install Matlab under Ubuntu 10.10. But it doesn't even go as far as the OP posted.

When I try to install  Matlab 2010b with 

sudo sh install

I get this 

dirname: fehlender Operand
&#8222;dirname --help&#8220; gibt weitere Informationen.
---------------------------------------------------------------------------
Error: Cannot locate Java Runtime Environment (JRE).
The directory /java/jre/glnx86/jre does not exist.

The weird thing is that that folder exsits in the .iso. So I'm kind of confused on what to do here. Can someone help?

thanks

I have the same problem. The syntax of *dirname* might have changed in the version of coreutils shiped with 10.10, or something similar.

The problem could probably be worked around by editing the install script but I haven't looked into that since octave works very well as a replacement for matlab.

---

### Post by thameera on 2010-10-29
1. You need to have sun java installed in your system. It's not in the 10.10 repositories, so I did it as in this: [http://goo.gl/Yewd](http://goo.gl/Yewd)
2. Make sure you give the correct sudo privileges.

FYI, here are the steps I used to install Matlab successfully: [http://goo.gl/vTd8](http://goo.gl/vTd8)

---

### Post by tschuliaen on 2010-11-24
ok this is weird.
i opened the install file with gedit... tried to edit something, so I guess you just need to edit any enter and save the file!

---

### Post by r_ivan87 on 2010-11-25
Hi.
For installing MatLab you can do very simple thing!
In directory MATLAB/java/jre/glnx86/jre/bin go in properties of file java. Tab "rights": click "permission allows the file as a program".
Enjoy.

---

### Post by m.hAMDy on 2010-12-21
i've had all sorts of problems with the installation,solving a problem only to be faced with another.
the install file is simply messed up and i've extracted the commands that do the real work from it.
it's important to highlight that i these commands are for Matlab R2010b which i use now.

cd to the directory where the install file resides then type the following commands:
```
mkdir -p /tmp/java/jar
cp -rf ./java/jar/* /tmp/java/jar
chmod -R +w /tmp/java/jar 2>/dev/null
mkdir -p /tmp/java/jarext
cp -rf ./java/jarext/* /tmp/java/jarext
chmod -R +w /tmp/java/jarext 2>/dev/null
sudo ./java/jre/glnx86/jre/bin/java -d32 -Djava.ext.dirs=./java/jre/glnx86/jre/lib/ext:/tmp/java/jar:/tmp/java/jarext -jar /tmp/java/jar/installwizard.jar -root . -javadir ./java/jre/glnx86/jre
```

i hope this starts the installation successfully.
notice the installation directory that will appear in the wizard and copy it's name somewhere.
make a shortcut on you desktop or panel ,and paste the name of the installation directory that you recorded where the shortcut requests 'command' and give it the -desktop option.

---

### Post by mazzatelli on 2010-12-25
I'm also trying to install Matlab 2010b, but on Ubuntu 10.04.

I try to run ./install script - I get similar error messages, but instead of permission denied I obtain:

```
Installing ...
/tmp/mathworks_22813/java/jre/glnx86/jre/bin/java: 1: &#65533;<&#65533;i&#65533;&#65533;1&#65533;ai&#65533;hY: not found
/tmp/mathworks_22813/java/jre/glnx86/jre/bin/java: 1: e&#65533;h/&#65533;%&#65533;M}&#65533;&#65533;&#65533;&#65533;Bh&#65533;_&#65533;&#65533;J&#65533;&#65533;X&#65533;Gc@&#65533;Z&#65533;&#65533;&#65533;: not found
/tmp/mathworks_22813/java/jre/glnx86/jre/bin/java: 6: cannot open 
                                                                  E&#65533;O&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;7&#65533;&#65533;&#65533;: No such file
/tmp/mathworks_22813/java/jre/glnx86/jre/bin/java: 11: B&#65533;&#65533;ZS&#65533;&#65533;&#65533;&#1996;4&#65533;&#65533;&#65533;: not found
&#65533;&#8127;pLRr&#65533;6yXB&#65533;&#65533;&#33943;T&#65533;>&#65533;0&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;6/jre/bin/java: 11: O&#538;Bk&#65533;u
J5M{n&#65533;&#65533;?&#65533;V&#65533;&#65533;Q    ^+&#65533;$=!&#65533;&#1636;&#65533;&#65533;&#65533;&#65533;ka&#65533;1
&#65533;&#65533;&#65533;&#65533;Q&#65533;&#65533;_&#1729;<&#65533;&#65533;&#65533;%&#65533;&#65533;&#65533;&#65533;w&#65533;)&#65533;h&#65533;&#65533;_&#65533;&#65533;q&#65533;&#65533;&#65533; &#65533;hP&#65533;&#65533;y}&#65533;K&#65533;&#65533;3&#65533;&#65533;&#65533;&#65533;¤'&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;w!&#1137;&#65533;
&#65533;&&#65533;&#65533;U&#65533;Gl\&#65533;s&#701;&#65533;&#65533;&#65533;$
<&#65533;&#65533;&#65533;&#265;&#65533;&#436;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;Y&#65533;&#65533;}&#65533;1i&#65533;&#65533;3: File name too long
/tmp/mathworks_22813/java/jre/glnx86/jre/bin/java: 11: /tmp/mathworks_22813/java/jre/glnx86/jre/bin/java: 12: Syntax error: word unexpected (expecting ")")&#65533;&#65533;&#955;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;B&#65533;&#65533;&#65533;LB&#1406;&#65533;&#65533;g&#65533;2#4&#65533;E&#65533;uj&#65533;: not found

Finished

```Does anyone have an idea what could be the issue?

EDIT: Okay, I found the solution to my problem - I had been using incorrect mount parameters

---

### Post by adib85 on 2011-01-03
I have the same problem here .. 
can you help me to solve it!!



> **mazzatelli said:**
> I'm also trying to install Matlab 2010b, but on Ubuntu 10.04.

I try to run ./install script - I get similar error messages, but instead of permission denied I obtain:

```
Installing ...
/tmp/mathworks_22813/java/jre/glnx86/jre/bin/java: 1: &#65533;<&#65533;i&#65533;&#65533;1&#65533;ai&#65533;hY: not found
/tmp/mathworks_22813/java/jre/glnx86/jre/bin/java: 1: e&#65533;h/&#65533;%&#65533;M}&#65533;&#65533;&#65533;&#65533;Bh&#65533;_&#65533;&#65533;J&#65533;&#65533;X&#65533;Gc@&#65533;Z&#65533;&#65533;&#65533;: not found
/tmp/mathworks_22813/java/jre/glnx86/jre/bin/java: 6: cannot open 
                                                                  E&#65533;O&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;7&#65533;&#65533;&#65533;: No such file
/tmp/mathworks_22813/java/jre/glnx86/jre/bin/java: 11: B&#65533;&#65533;ZS&#65533;&#65533;&#65533;&#1996;4&#65533;&#65533;&#65533;: not found
&#65533;&#8127;pLRr&#65533;6yXB&#65533;&#65533;&#33943;T&#65533;>&#65533;0&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;6/jre/bin/java: 11: O&#538;Bk&#65533;u
J5M{n&#65533;&#65533;?&#65533;V&#65533;&#65533;Q    ^+&#65533;$=!&#65533;&#1636;&#65533;&#65533;&#65533;&#65533;ka&#65533;1
&#65533;&#65533;&#65533;&#65533;Q&#65533;&#65533;_&#1729;<&#65533;&#65533;&#65533;%&#65533;&#65533;&#65533;&#65533;w&#65533;)&#65533;h&#65533;&#65533;_&#65533;&#65533;q&#65533;&#65533;&#65533; &#65533;hP&#65533;&#65533;y}&#65533;K&#65533;&#65533;3&#65533;&#65533;&#65533;&#65533;¤'&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;w!&#1137;&#65533;
&#65533;&&#65533;&#65533;U&#65533;Gl\&#65533;s&#701;&#65533;&#65533;&#65533;$
<&#65533;&#65533;&#65533;&#265;&#65533;&#436;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;Y&#65533;&#65533;}&#65533;1i&#65533;&#65533;3: File name too long
/tmp/mathworks_22813/java/jre/glnx86/jre/bin/java: 11: /tmp/mathworks_22813/java/jre/glnx86/jre/bin/java: 12: Syntax error: word unexpected (expecting ")")&#65533;&#65533;&#955;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;B&#65533;&#65533;&#65533;LB&#1406;&#65533;&#65533;g&#65533;2#4&#65533;E&#65533;uj&#65533;: not found

Finished

```Does anyone have an idea what could be the issue?

EDIT: Okay, I found the solution to my problem - I had been using incorrect mount parameters

---

### Post by lijianch on 2011-02-22
This is the X problem. You can simply login as root. 

Before running the install script. 

run the following command

xauth merge .Xauthority

That is it.

---

### Post by mazzatelli on 2011-04-08
> **adib85 said:**
> I have the same problem here .. 
can you help me to solve it!!

The way I solved it was because there was something wrong with the way I mounted the .iso file.
I was using Furius ISO mount, when you should use:
```
sudo mount debianetch.iso /media/isoimage/ -t iso9660 -o loop
```

Then the install should work properly

---

### Post by gharibi on 2011-04-23
Well, it's more than 4 days now since I have downloaded that massive iso for MATLAB R2010B and still can't figure out how to get the installer to run on Ubuntu 10.10. I tried to run the installer as explained in the included pdf:

>sudo sh /media/cdrom/MATHWORK_R2010B/install &
or:
sudo sh /media/cdrom/MATHWORKS_R2010B/./install

but the installer doesn't initiate giving a list of 100 error messages with java. I tired to change the permission for the java file at: MATHWORKS_R2010B/java/jre/glnx86/jre/bin but still have the same issue. 

This is a portion of the list of errors the installer ended with:

cp: reading `/media/MATHWORKS_R2010B/java/jarext/dws-client-v3.jar': Input/output error
cp: reading `/media/MATHWORKS_R2010B/java/jarext/geronimo-stax-api.jar': Input/output error
cp: reading `/media/MATHWORKS_R2010B/java/jarext/glazedlists_java15.jar': Input/output error
cp: reading `/media/MATHWORKS_R2010B/java/jarext/guice.jar': Input/output error
cp: reading `/media/MATHWORKS_R2010B/java/jarext/jaccess-1_4.jar': Input/output error
cp: reading `/media/MATHWORKS_R2010B/java/jarext/jdom.jar': Input/output error
cp: reading `/media/MATHWORKS_R2010B/java/jarext/mail.jar': Input/output error
cp: reading `/media/MATHWORKS_R2010B/java/jarext/neethi.jar': Input/output error
cp: reading `/media/MATHWORKS_R2010B/java/jarext/wsdl4j.jar': Input/output error
cp: reading `/media/MATHWORKS_R2010B/java/jarext/wstx-asl.jar': Input/output error
cp: reading `/media/MATHWORKS_R2010B/java/jarext/xercesImpl.jar': Input/output error
cp: reading `/media/MATHWORKS_R2010B/java/jarext/xml-apis.jar': Input/output error
Installing ...
Finished

I would really appreciate any ideas!

Thanks,

Zaher

---

### Post by hennessy.matt on 2011-05-02
I am basically having the same problem! However, for me it is with Ubuntu 11.04 and MATLAB R2011a!


> **gharibi said:**
> Well, it's more than 4 days now since I have downloaded that massive iso for MATLAB R2010B and still can't figure out how to get the installer to run on Ubuntu 10.10. I tried to run the installer as explained in the included pdf:

>sudo sh /media/cdrom/MATHWORK_R2010B/install &
or:
sudo sh /media/cdrom/MATHWORKS_R2010B/./install

but the installer doesn't initiate giving a list of 100 error messages with java. I tired to change the permission for the java file at: MATHWORKS_R2010B/java/jre/glnx86/jre/bin but still have the same issue. 

This is a portion of the list of errors the installer ended with:

cp: reading `/media/MATHWORKS_R2010B/java/jarext/dws-client-v3.jar': Input/output error
cp: reading `/media/MATHWORKS_R2010B/java/jarext/geronimo-stax-api.jar': Input/output error
cp: reading `/media/MATHWORKS_R2010B/java/jarext/glazedlists_java15.jar': Input/output error
cp: reading `/media/MATHWORKS_R2010B/java/jarext/guice.jar': Input/output error
cp: reading `/media/MATHWORKS_R2010B/java/jarext/jaccess-1_4.jar': Input/output error
cp: reading `/media/MATHWORKS_R2010B/java/jarext/jdom.jar': Input/output error
cp: reading `/media/MATHWORKS_R2010B/java/jarext/mail.jar': Input/output error
cp: reading `/media/MATHWORKS_R2010B/java/jarext/neethi.jar': Input/output error
cp: reading `/media/MATHWORKS_R2010B/java/jarext/wsdl4j.jar': Input/output error
cp: reading `/media/MATHWORKS_R2010B/java/jarext/wstx-asl.jar': Input/output error
cp: reading `/media/MATHWORKS_R2010B/java/jarext/xercesImpl.jar': Input/output error
cp: reading `/media/MATHWORKS_R2010B/java/jarext/xml-apis.jar': Input/output error
Installing ...
Finished

I would really appreciate any ideas!

Thanks,

Zaher

---

### Post by m.hAMDy on 2011-05-05
has anybody tried the instructions i listed above?

---

### Post by safaroth on 2011-06-04
> **Tandrial said:**
> 
dirname: fehlender Operand
&#8222;dirname --help&#8220; gibt weitere Informationen.
---------------------------------------------------------------------------
Error: Cannot locate Java Runtime Environment (JRE).
The directory /java/jre/glnx86/jre does not exist.


I had similar problem. And I found out a solution at Mathworks Support. 
It happens when the path to iso has spaces. I didn't get this error once I mounted my iso to \media\matlab and installed from there

---

### Post by safaroth on 2011-06-04
> **3rd said:**
> 

eval: 1: /tmp/mathworks_15227/java/jre/glnxa64/jre/bin/java: Permission denied



And ya, I also faced this one... It happens when you unzip or extract the iso in Windows and use those extracted files in Linux for installation. I extracted using Linux GUI but even then it wasn't working. Finally, i mounted through the terminal and it worked fine

sudo mkdir /media/matlab
sudo -o loop /[iso path]/matlab2010b_64.iso /media/matlab


btw, I have Linux Mint 11 installed and am using student version of Matlab2010b for 64bit Linux

---

### Post by pksadiq on 2011-06-04
You might also consider the GNU Octave which is highly compatible with Matlab codes. visit [http://www.gnu.org/software/octave/ ]("http://www.gnu.org/software/octave/")
and also check their docs there

also [http://www.gnu.org/software/octave/FAQ.html#MATLAB-compatibility](http://www.gnu.org/software/octave/FAQ.html#MATLAB-compatibility)

You may install it :
```
sudo apt-get install octave3.2
```:)

---

### Post by BongoBen on 2011-07-01
I just had a lot of problems getting the installer running for Matlab R2011a. I'm using Ubuntu 10.10 with the 64-bit version. Here's what I did to get it working:

1) From the install directory, go to the following java directory and make everything executable:
cd ./java/jre/glnxa64/jre/bin/
chmod a+x *

2) From the install directory again, go to ./bin/glnxa64. You will need to delete the libstdc++.so.6 file, as it is a bad symbolic link. I just made it link to my current libstdc++.so.6:
cd ./bin/glnxa64
rm libstdc++.so.6
ln -s /usr/lib/libstdc++.so.6 .

That's it! Hopefully this works for others.

---

### Post by nazclarion on 2011-08-24
> **3rd said:**
> Hello,

I am a complete Ubuntu novice so please be kind!
I have just installed 10.10 (64 bit) and am trying to install MATLAB r2010b.
I execute the MATLAB install file (as root) and I get the following output:

Preparing installation files ...
Installing ...
eval: 1: /tmp/mathworks_15227/java/jre/glnxa64/jre/bin/java: Permission denied

Could anyone advise me why I get this error and how I can make the install work?
Thanks,

3rd


1. In /etc/fstab change:

*"tmpfs		/tmp		tmpfs	defaults,noexec,nosuid	0	0"*

To :

*"tmpfs		/tmp		tmpfs	defaults	0	0"*

2. Run *mountall* in terminal
3. Install Matlab
4. In /etc/fstab change:

*"tmpfs		/tmp		tmpfs	defaults	0	0"*

To :

*"tmpfs		/tmp		tmpfs	defaults,noexec,nosuid	0	0"*

5. Run *mountall* in terminal
6. Play the guitar  :guitar:

!!! Don't forget to put back [[COLOR="Blue"]_**noexec** and **nosuid**_[/COLOR]]("http://www.cyberciti.biz/tips/the-importance-of-linux-partitions.html") options after Matlab installation. !!!

---

### Post by jr226 on 2011-09-28
FYI: [http://www.mathworks.com/support/solutions/en/data/1-EBY5E6/index.html?product=SL&solution=1-EBY5E6](http://www.mathworks.com/support/solutions/en/data/1-EBY5E6/index.html?product=SL&solution=1-EBY5E6)

No spaces allowed in install path.

---

