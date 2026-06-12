---
title: "get out of grub"
date: 2010-11-24
forum: General Help
---

### Post by imu96 on 2010-11-24
i run a dual boot system of vista and kubuntu and when i tried to go into linux i accidentally went into grub and now i don't know how to get out of grub....
 
please help...
 
i looked for a solution all over the internet but either they didn't work or there is something preventing me from using them (like one involves a live cd but i don't have one and i can't make one as my internet is too slow...

---

### Post by imu96 on 2010-11-28
i'm starting to really hate grub....

---

### Post by Dave_L on 2010-11-28
I'm not sure what you mean by "get out of grub".

Are you at the grub command prompt?

---

### Post by imu96 on 2010-11-28
i think that's what it's called... when i boot up my laptop- i get two options: windows or kubuntu

when i picked kubuntu i USED to get a list of generic ubuntu and recovery ubuntu (i will refer to this as the ubuntu menu). if i selected the generic one it would take me to the ubuntu login screen.

but then i accidently pressed something and from the ubuntu list it took me to a grub thingy and it says 

"grub>"

and then it says that if you press tab it will give you a list of the first words for grub but it doesn't tell me how to go back to the ubuntu menu so i can go to the login screen... so how do i do that????

things that i have tried and results:

exit: takes me back to choosing between windows and kubuntu

quit: doesn't do anything

exit grub: same as exit

(the escape button): makes another goes on to the next line (grub<)

and some stuff like root (hd0,1): but that only told me that co- ordinates file system type

---

### Post by imu96 on 2010-11-29
plz dont leave me hangin....

---

### Post by Paanini on 2010-11-29
Usually pressing 'c' at the grub menu takes you to the grub command prompt.
You may have inadvertently pressed 'c' at some point - try pressing 'c' again.

Did you take a look at the Community Documentation for Grub2 ?

[https://help.ubuntu.com/community/Grub2#Rescue%20Mode](https://help.ubuntu.com/community/Grub2#Rescue%20Mode)

---

### Post by imu96 on 2010-11-29
pressing c doesn't work...

i'm just about 2 try the command summary from the link you sent me because i don't understand anything... i just know how to type. :confused:

but thanks for your help!!! any is appreciated!!! :)

---

### Post by imu96 on 2010-11-29
it didn't work... i had no idea wat is was doing... and half the time it kept telling me file not found

btw what's wubi because it told me to subustitute something in for steps 3 and 7 if it was within windows... does that mean if it's virtualised inside windows or dual boot with it??

speaking of substitution... how do i know what numbers to substitute in for X and Y in (hdX,Y).

plz reply soon i'm having 2 use windows!! ;)

---

### Post by Paanini on 2010-11-29
Have you installed Kubuntu as a separate OS on a diff partition (other than windows) ? If you have, then you needn't worry about Wubi.

A similar thing had happened to me when I'd first installed BURG on Ubuntu. What I'd done wrong was that I'd forgotten to update the burg.cfg file. Maybe you could try updating your GRUB with ```
sudo update-grub
``` ?

(hdX, Y) is a notation equivalent to sdaY used to denote partitions on your hard drive.
The first hard disk is usually called 'sda' or hd0. Any second drive will be given by sdb or hd1.
The second number refers to a partition. So if your drive has 4 partitions, they'll be numbered sda1, sda2, sda3, sda4 or (hd0,1), (hd0,2) etc...

I think```
 ls -l 
```should give you a list of all partitions and their filesystems. Look for the one that has type as 'Linux' or etx3 / ext4. That's the one you should remember.

Check out this link, this guy was getting the grub command line too, although he was using BURG, I think the commands should remain the same.

[https://answers.launchpad.net/burg/+question/99357](https://answers.launchpad.net/burg/+question/99357)

You'll have to replace sda1 by whatever is relevant to you. (i.e. - the location of your ext3 / ext4 filesystem).
But first, I'd suggest go back to the community documentation page and read it once again :)

---

### Post by oldfred on 2010-11-30
Do you have a liveCD that you can boot? 

If so download and run this script so we can see your exact configuration.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] here [ /code] tags.

---

### Post by imu96 on 2010-11-30
i don't have a live cd cuz i got my linux off sum1 during the holidays while i was visiting....

---

### Post by Hippytaff on 2010-11-30
Can you download the iso and burn a live cd?
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

---

### Post by imu96 on 2010-11-30
internet's too slow... gmail complains!!!

what about a fedora 12 live cd cuz i hav 1 of those....

---

### Post by imu96 on 2010-11-30
i tried sudo update-grub but that didn't work as it didn't understand any of it....

i typed in ls -l but then i was just like.... ok now what do i type...

---

### Post by Hippytaff on 2010-11-30
If you can boot with any live cd and post the results.txt as oldfred suggested in post #10 then that would help identify the problem :-)
 
Ubuntu livecd's come free with almost any Linux magazine and you can order them online for free :-)

---

### Post by imu96 on 2010-11-30
i don't get what oldfred means when he says lets "lets c what the configuration is" ??? like... once i boot the cd... what do i do???

sorry for being so cluless about linux i've only been using it for a few months now so i don't know much...

again... thanks for all your help....

---

### Post by Hippytaff on 2010-11-30
no worries...boot with a live cd and choose try rather than install. then go to this link
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)
Download the script and run it as per the instructions. Then a RESULTS.TXT should appear on the desktop. Post that here. It will show your boot configuration and all the gubbins that will help people try to help you fixthe boot problem :-)

---

### Post by imu96 on 2011-02-27
ya.... actually i think somehow my kubuntu deleted itself cuz when i plugged in my ubuntu live usb (that i just recently made) i typed in exit it took me into the live usb's ubuntu

but as i said.... if i just typed in exit.... it took me bak to the thing where i choose either kubuntu or windows....

so in other words.... my kubuntu deleted itself from one computer so i got another computer and wiped out the windows dos on it and ubuntu completely took it over....

i'm going 2 mark this thread as solved now.... :)

---

