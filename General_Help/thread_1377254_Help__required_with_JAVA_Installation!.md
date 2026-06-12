---
title: "Help  required with JAVA Installation!"
date: 2010-01-10
forum: General Help
---

### Post by Saurabhdua on 2010-01-10
Hello There!:D

My Both browsers viz. Firefox & Chrome are devoid of JAVA Installation & hence not able to run any Applet application & hence forth!

With reference to the attached Screenshot, I have downloaded the option No.-2 & not able to perform anything significant with it?

On double click, it do not reacts...& hence wish to seek any assistance in this regard.:(

[B][U]Enclosures:::Screenshots of download options & Downloaded file.
[/U][/B]

---

### Post by 3rdalbum on 2010-01-10
You don't need to download anything from a website to get Java.

Just install the "sun-java6-jre" and "sun-java6-plugin" packages from Synaptic Package Manager.

Besides, the program you downloaded needs to be made executable (given execute permission) and then run as root on the command-line. Which is why it's easier just to get it from your package manager.

---

### Post by dxxvi on 2010-01-10
Your jre file is ok, but I never work with it so I cannot give the exact instructions. If you don't mind download a bigger java file then ...

1. Download java from here [http://java.sun.com/javase/downloads/widget/jdk6.jsp](http://java.sun.com/javase/downloads/widget/jdk6.jsp). Your downloaded file will be jdk-6u17-linux-i586.bin

2. chmod +x jdk-6u17-linux-i586.bin

3. ./jdk-6u17-linux-i586.bin

4. optional: you can move the jdk1.6.0_17 to anywhere (e.g. you move it to your home directory with mv jdk1.6.0_17 ~)

5. mkdir ~/.mozilla/plugins

6. cd ~/.mozilla/plugins

7. ln -s ~/jdk1.6.0_17/jre/plugin/i386/ns7/libjavaplugin_oji.so

8. restart your browser and you're good to go.

---

### Post by Saurabhdua on 2010-01-10
Thanks...BUT I don know what's going wrong over here? I was able to mark the choices as specified by you & a click on 'Apply' button took me to a 'Download' Screen, went on successfully BUT couldn't see anywhere as "Applying or Installing" the packages??!

On making an attempt to exit the Synaptic Manager, it says changes will be undone or somewhat like that..?!

Its really turning out to be a erratic experience(yet again..!) & FRANKLY such things take me back to Windows persistently...

What next..Sir?

---

### Post by scouser73 on 2010-01-10
For installing the 32 & 64 bit version of Java please follow the instructions [[COLOR="Red"]**Here**[/COLOR]]("http://sites.google.com/site/easylinuxtipsproject/java")

Although on the site it states that it's only for Ubuntu 9.10, I have installed it on Ubuntu 9.04 and it works flawlessly.

---

### Post by Saurabhdua on 2010-01-11
Thanks for your Reply..Scouser..BUT then I think that Iam quite better off 'Without' JAVA..!

Who'll gonna be MAD to that extent to perform this 'Religious Ceremony' with all Bells & Whistles?...Its OK with me..!

By the way, Iam still with 9.04 since couldn't yet make my Internet Connection(which used with Bridge mode settings rather than PPPoE/oA) work with Karmic.

Hope some Gr8 & Nice Ideas will germinate within UBUNTU Community to make it favorable for mass adoption. For now, it seems to be a DISTANT DREAM!

---

### Post by 3rdalbum on 2010-01-11
Can you please describe exactly what happens? After the download finishes, a window will pop up asking you to accept the license agreement. Accept it and the installing will finish.

Once you've got your head around using the repositories instead of trawling the web, everything will fall into place. Keep at it.

---

### Post by Saurabhdua on 2010-01-12
Nothing appeared once the Downloading finished. Screen just vanished away!?
If Iam not wrong, 36MB of files were downloaded & 104MB of Disk space were to be used!

However, I made a 'Tick' on "Download Package Files only".Does it has anything to do with something?

What Next?

---

### Post by wojox on 2010-01-12
Open a terminal and type or copy and paste this:

```
sudo apt-get install sun-java6-jre sun-java6-plugin
```

[http://wojox.homelinux.net/?p=16](http://wojox.homelinux.net/?p=16)

---

### Post by Saurabhdua on 2010-01-14
Hello again!

I did what you told me to & now it shows up this screen(Pls refer to the attachment)?

NO option shows up to proceed ahead & neither ENTER works with it.Moreover, CPU is not showing up any activity!?

Any light ahead?

---

### Post by Yellow Pasque on 2010-01-14
Use the tab key to highlight 'OK' and then press Enter...

---

### Post by Saurabhdua on 2010-01-17
Hello Dear!

_**Luck runs out again..since I get this thing as an Output::::::**_

saurabhdua@saurabhdua-desktop:~$ sudo apt-get install sun-java6-jre sun-java6-plugin
[sudo] password for saurabhdua: 
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
saurabhdua@saurabhdua-desktop:~$ sudo dpkg --configure -a
Setting up java-common (0.30ubuntu4) ...

Processing triggers for man-db ...
Processing triggers for doc-base ...
Processing 2 added doc-base file(s)...
Registering documents with scrollkeeper...
saurabhdua@saurabhdua-desktop:~$ sudo apt-get install sun-java6-jre sun-java6-plugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  sun-java6-jre: Depends: sun-java6-bin (= 6-16-0ubuntu1.9.04) but it is not going to be installed or
                          ia32-sun-java6-bin (= 6-16-0ubuntu1.9.04) but it is not installable
                 Recommends: gsfonts-x11 but it is not going to be installed
  sun-java6-plugin: Depends: sun-java6-bin (= 6-16-0ubuntu1.9.04) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
saurabhdua@saurabhdua-desktop:~$

---

