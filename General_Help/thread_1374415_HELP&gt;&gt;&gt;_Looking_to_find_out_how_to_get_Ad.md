---
title: "HELP&gt;&gt;&gt; Looking to find out how to get Adobe on Ubuntu"
date: 2010-01-06
forum: General Help
---

### Post by Unhubbed on 2010-01-06
[SIZE=2]**I have recently installed Ubuntu 9.04 on My Acer aspire one D250-1842, and Im haveing trouble finding and loading Adobe Reader on my pC. Help Please. Thanks**[/SIZE]

---

### Post by mikewhatever on 2010-01-06
Adobe reader should be in the partner repository. Go to System->Admin->Software-Sources, select 'Other Software' tab and check the partner repository box. Reload when prompted and then install the reader. Needless to say, gedit is a much better program present by default, but well, it's not Adobe.

---

### Post by metalf8801 on 2010-01-06
Have you tried searching for Adobe Reader in Add/remove?

---

### Post by Unhubbed on 2010-01-06
Heres what I see, and I dont see the "other" ... does the pic help?[IMG]file:///home/gary/Desktop/Screenshot.png[/IMG][IMG]http://file:///home/gary/Desktop/Screenshot.png[/IMG]

---

### Post by slakkie on 2010-01-06
Evince, kpdf, xpdf, etc. You don't need the software from Adobe to view PDF's :)


aptitude search pdf and you'll get a whole list of PDF viewers (and more).

---

### Post by Unhubbed on 2010-01-06
I cant seem to find anything regardind adobe anywhere on my ubuntu program 9.04

---

### Post by slakkie on 2010-01-06
Could you execute the following command?

```

echo -e "#Partner repository\ndeb http://archive.canonical.com/ubuntu $(lsb_release -cs) partner" | sudo tee -a /etc/apt/sources.list
sudo aptitude update
aptitude search adobe  

```

---

### Post by Unhubbed on 2010-01-06
root@gary-laptop:/home/gary# echo -e "#Partner repository\ndeb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) $(lsb_release -cs) partner" | sudo tee -a /etc/apt/sources.list
#Partner repository
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
root@gary-laptop:/home/gary# sudo aptitude update
Writing extended state information... Done
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release.gpg                            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Translation-en_US                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release.gpg
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Translation-en_US  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages                    
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Packages                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Sources
Reading package lists... Done             

root@gary-laptop:/home/gary# aptitude search adobe




Ok thats done..  now what do i do?

---

### Post by scouser73 on 2010-01-06
**1** - Go to the [[COLOR="Red"]**Adobe Reader Website**[/COLOR]]("http://get.adobe.com/uk/reader/?promoid=BUIGO")
**2** - Click on **Different Language Or Operating System**
**3** - Click on the **Select An Operating System** drop down menu
**4** - Select **Linux - x86 (.deb)**
**5** - Click **Continue**
**6** - Select **Adobe Reader 9.2** & Click **Download Now**
**7** - Open With **GDebi Package Installer**

If the **GDebi Package Installer** isn't showing then save the file to your desktop and install it that way.

That will start installing Adobe PDF Reader for you, once installed you can find it in the Office menu.

---

### Post by tekkidd on 2010-01-06
DOWNLOAD IT [http://get.adobe.com/uk/reader/?promoid=BUIGO](http://get.adobe.com/uk/reader/?promoid=BUIGO)

THEN 

cd into the directory 

THEN 

chmod a+x filename

THEN 

./filename 

DONE

--------------------------
Personally i prefer okular

---

### Post by Unhubbed on 2010-01-06
ok the gdeb installer is downloading it, what will i need to do to get it working from there?

---

### Post by scouser73 on 2010-01-06
Just follow the instructions as shown really, it'll appear in Office.

---

### Post by slakkie on 2010-01-06
> **Unhubbed said:**
> 
root@gary-laptop:/home/gary# aptitude search adobe


Sorry, acroread. 

```

$ apt-cache policy acroread
acroread:
  Installed: (none)
  Candidate: 9.2-1karmic1
  Version table:
     9.2-1karmic1 0
        990 http://archive.canonical.com karmic/partner Packages
     9.1.0-7jaunty2 0
        990 http://archive.canonical.com lucid/partner Packages

```

---

### Post by Unhubbed on 2010-01-06
[B]Thanks so much, everything here worked great..Thank you!!


[/B] 				**Re: HELP>>> Looking to find out how to get Adobe on Ubuntu** 			 			 			 		   		 		 		**1** - Go to the [[COLOR=Red]**Adobe Reader Website**[/COLOR]]("http://get.adobe.com/uk/reader/?promoid=BUIGO")
**2** - Click on **Different Language Or Operating System**
**3** - Click on the **Select An Operating System** drop down menu
**4** - Select **Linux - x86 (.deb)**
**5** - Click **Continue**
**6** - Select **Adobe Reader 9.2** & Click **Download Now**
**7** - Open With **GDebi Package Installer**

If the **GDebi Package Installer** isn't showing then save the file to your desktop and install it that way.

---

### Post by drpjkurian on 2010-01-06
Hi
I do not use addobe reader to read pdf files. I use either KPDF or evince to read my pdf. I am using these programmes for years.

Dr Kurian

---

### Post by mikewhatever on 2010-01-07
This is probably related to Windows, but interesting nevertheless.
[http://www.computerworld.com/s/article/9142388/Adobe_won_t_patch_latest_PDF_zero_day_until_Jan._12](http://www.computerworld.com/s/article/9142388/Adobe_won_t_patch_latest_PDF_zero_day_until_Jan._12)

---

