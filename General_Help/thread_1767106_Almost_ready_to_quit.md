---
title: "Almost ready to quit"
date: 2011-05-25
forum: General Help
---

### Post by Kenc3 on 2011-05-25
I downloaded Ubuntu 11.04 about a week ago and have been reading and trying things ever since. 
I tried to get my old Windows programs to work even though I knew about the ones on Ubuntu. 
I tried to get programs to work that are supposed to be for Linux but those also did not work. I have not had anything work except those on the Software list that comes with the program. 
I have been trying to get storybook or ywriter to work with no luck. 
I even looked up the commands using the command lines. that didn't work either.
I am almost at the end. There are no schools here that speak English or are not expensive. There doesn't seem to be any users in the area. 
Maybe I should just go back to Windows and stay there. I just cannot seem to figure this out.:confused:

---

### Post by Grenage on 2011-05-25
You will have to be specific with your problems, and let people help you with them one at a time.  That said, using Windows is not a bad thing; you should use whatever benefits you the most.

---

### Post by Kenc3 on 2011-05-25
I have several threads already with the specific problems. I loaded wine, I found out that virtualbox comes with ubuntu, I even changed the permissions on one of my windows programs that I knew would be okay but then it is blocked by Linux because it was downloaded with the wrong site.
I tried to install storybook which is spposed to be a Linux program and it just sits there in the download box and doesn't go anywhere. I cannot open that one either. 
Maybe I will find a way later but, for now, I will stay where I am and just go to Linux when I have extra time or think up a new idea.
Ihave two books on Ubuntu 11.04 and when I follow those it still doesn't want to work for me. 
Maybe I am just too old to learn.

---

### Post by webofunni on 2011-05-25
> **Kenc3 said:**
> I downloaded Ubuntu 11.04 about a week ago and have been reading and trying things ever since. 
I tried to get my old Windows programs to work even though I knew about the ones on Ubuntu.

You cannot execute windows exe files in Linux unless you are using emulators like Wine 

[http://en.wikipedia.org/wiki/Wine_%28software%29](http://en.wikipedia.org/wiki/Wine_%28software%29)

> 
I tried to get programs to work that are supposed to be for Linux but those also did not work. I have not had anything work except those on the Software list that comes with the program.

You need to install the software that you want before start using it. Can you share the program that you are trying to install/start ? 

> 
I have been trying to get storybook or ywriter to work with no luck.


To install yWriter, do

1. Login to Ubuntu. press ALT+F2 and enter gnome-terminal press enter. Then execute below command ( You need to be connected to internet )

```

sudo apt-get install libmono-microsoft-visualbasic8.0-cil ttf-mscorefonts-installer

``` 

That will take some time. 

After that. Execute below commands one by one

```

wget http://www.spacejock.com/files/yWriter5.zip
unzip yWriter5.zip 
cd yWriter5/bin/
mono yWriter5.exe

```

That should start the program. 

> 
I even looked up the commands using the command lines. that didn't work either.

Which commands that you are trying ? What is the error/message that you are getting ? 

> 
I am almost at the end. There are no schools here that speak English or are not expensive. There doesn't seem to be any users in the area. 
Maybe I should just go back to Windows and stay there. I just cannot seem to figure this out.:confused:

Please explain the issues that you are facing with the error/messages that you are getting, so that we can help.

---

### Post by webofunni on 2011-05-25
For storybook. You can do...

1. Login to Ubuntu. Press ALT+F2 enter gnome-terminal and press enter. Execute the below commands one by one in the terminal window. 

```

sudo apt-get install openjdk-6-jre openjdk-6-jre-headless
wget http://downloads.sourceforge.net/project/storybook2/storybook/2.1.16/storybook-2.1.16-linux.bin
chmod 755 storybook-2.1.16-linux.bin
./storybook-2.1.16-linux.bin
~/opt/storybook/storybook

```

copy and past the messages from the terminal, if you are facing any problem.

---

### Post by Kenc3 on 2011-05-25
Unni-that seemed to work. I forgot to get rid of the old copy of yWriter and it is still on the comuter apparently. Where is the one that I run?
My 6 year old wants me right now so I will be away for a few hours and then I will try the storybook install.
Thanks. I will check back if I have more problems.
I was using ctrl-alt-F1 before. Is that different from Alt-F2?

---

### Post by webofunni on 2011-05-25
Current yWriter should be in your home folder. You can see the folder yWriter5. Are you able to see that ? 

You might have find the diff between CTRL+ALT+F1 and ALT+F2. The first one will open the console. That is command line interface without graphical desktop. The second one will open Gnome terminal that is a graphical terminal runs within the desktop.

---

### Post by Petrolea on 2011-05-25
> **Kenc3 said:**
> Unni-that seemed to work. I forgot to get rid of the old copy of yWriter and it is still on the comuter apparently. Where is the one that I run?
My 6 year old wants me right now so I will be away for a few hours and then I will try the storybook install.
Thanks. I will check back if I have more problems.
I was using ctrl-alt-F1 before. Is that different from Alt-F2?

Alt + F2 is same as 'Run' on windows, it has nothing to do with Ctrl+alt+F1.

---

### Post by Kenc3 on 2011-05-25
I have two yWriter5 one is a bin and the other is a .zip
There is also a copy that is opened as a result of those commands. 
Sort of went from none to many. I guess that is good if I can figure out which one to get rid of and which one to keep.

---

### Post by webofunni on 2011-05-25
You can delete the zip package. That is not necessary.

---

### Post by Kenc3 on 2011-05-25
I deleted that one. Working on the Storybook now. 
I forgot my son had a birthday the other day. He is 7. I need to put him to sleep now. I will be back in awhile.

---

### Post by Kenc3 on 2011-05-25
Storybook is running fine now. 
yWriter is still a folder and a lot of small programs. Maybe I need to get rid of it completely and start all over again. It did open one time when I first installed it but after that the icon is missing.

---

### Post by webofunni on 2011-05-25
Do not remove yWriter directory. Do this 

1. Right click on desktop
2. Select Create launcher
3. Enter

Name : yWriter
Command : 

Click on Browse button. Click on yWriter5 folder and then on bin folder and then yWriter5.exe. 

You will see something like

/home/YOUR-USER-NAME/yWriter5/bin/yWriter5.exe

change that to

mono /home/YOUR-USER-NAME/yWriter5/bin/yWriter5.exe

4. Clock OK
5. You will see an Icon in your desktop named yWriter. Click on that to open it.

---

### Post by Kenc3 on 2011-05-25
Now that I have yWriter5 as a binary folder in the Home folder, how do I get it to become a desktop icon that I can click on and open like the storybook one?

---

### Post by Kenc3 on 2011-05-25
I got the following error message when I tried to ad mno to the create launcher.
 Details: Failed to execute child process "mono/home/ken/yWriter5/bin/yWriter5.exe" (No such file or directory)

---

### Post by Kenc3 on 2011-05-25
I found the mistake. I forgot to add a space after mono. Now I have two shortcuts on the desktop.  I must get rid of one of them.
I trashed the bad icon and emptied the trash. Opened yWriter5 so it is working fine. Storybook is now working fine. 
It is after 11PM here. I am usually in bed by now. I have been doing this all day and tomorrow I can finally try to remember what I was going to write about.(LOL) I have some files on the windows side I am going to bring over on a pen drive. Hopefully I won't have a problem with that.
Thanks to everyone for all the help. I think these programs will fill my needs. I may have to get storybook pro later.

---

### Post by webofunni on 2011-05-25
glad to know that its working :-). Please mark this thread as solved

---

### Post by dmcfarland on 2011-05-26
> **Kenc3 said:**
> I downloaded Ubuntu 11.04 about a week ago and have been reading and trying things ever since. 
I tried to get my old Windows programs to work even though I knew about the ones on Ubuntu. 
I tried to get programs to work that are supposed to be for Linux but those also did not work. I have not had anything work except those on the Software list that comes with the program. 
I have been trying to get storybook or ywriter to work with no luck. 
I even looked up the commands using the command lines. that didn't work either.
I am almost at the end. There are no schools here that speak English or are not expensive. There doesn't seem to be any users in the area. 
Maybe I should just go back to Windows and stay there. I just cannot seem to figure this out.:confused:

Stick with it. I am trying to ween off of Windows. Linux can be irritating sometimes. It is satisfying to overcome a problem or figure something out.

---

