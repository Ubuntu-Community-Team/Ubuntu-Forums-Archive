---
title: "Newbie questions audacity"
date: 2012-03-16
forum: General Help
---

### Post by jones27557 on 2012-03-16
Hello folks.  I am a newbie here.  I have installed ubuntu on my laptop and seems to be running well.  I am trying to learn ubuntu in order to migrate away from windows.

My question is that I have a lot of mp3's from what I have learned they are not supported in ubuntu but need to be converted to ogg files.  I downloaded audacity and unzipped it.  Now what do I do?

I chose the default location in the unpacking because I don't know enough about  ubuntu to know where I want to unzipp it to.  But I found the folder where it was unzipped to and there are a lot of folders and files in there.  I am stopped because I don't know what to do to make audacity install.  In windows there is a setup file that you click to install.  What is the equivalent in ubuntu?

In the package I have several folders: dox2-src, help, images, lib_src, locale, m4, mac, nyquist, plug.ins, present, src, and win.  There are also other files: aufacity.dox, autogen.sh, config.guess, config.sub, readme.txt, configure, configure.in, install.sh, license, makefile.in.

I clicked on install.sh and I got the pop up window "do you want to run or display content?"  The options were run, run in terminal, display, or cancel.    I clicked cancel because I don't know what I am doing.

Thanks for any help you can give on how to install audacity.

---

### Post by squilookle on 2012-03-16
You can play mp3s on Ubuntu: 

More information [here]("https://help.ubuntu.com/community/RestrictedFormats") and [here]("https://en.wikipedia.org/wiki/Ubuntu-restricted-extras")

You could convert your mp3s to OGG if you wanted to, but that would take a lot more time and effort.

---

### Post by jones27557 on 2012-03-16
Hey thanks a lot.  I'd much rather leave them as MP3 instead of converting them.  I just don;t know very much about ubuntu.  Thanks for the link I will go read up on it.

---

### Post by ajgreeny on 2012-03-16
Audacity is in the repos (or it was, at any rate) so why are you using an archive to install it?

---

### Post by jones27557 on 2012-03-16
I downloaded it because I don't know what a repos is.  If it is already installed than where/how do I find it?  I updated something and now the mp3s play.  I think it was called a restricted something and now the mp3's play in the Banshee player.

---

### Post by yetiman64 on 2012-03-16
Audacity will not be already installed, you will need to install it. 

The repositories can be set up in Software Sources. If on 11.04 or higher open dash and search for "software" (without the quotes), click on the Sofware Sources icon and check all the repositories are enabled. See screenshot attached.

Once closed, run this commands in terminal (ctrl+alt+t to open a terminal)
```
sudo apt-get update && sudo apt-get install audacity
``` This will do a system update and then install audacity. Once finished search for audacity in dash and launch from there. Let us know if you are on 10.10 or lower as dash isn't used in those, if this is the case it will be under Sound and Video in the menus.

---

### Post by jones27557 on 2012-03-16
Thanks yetiman.  I did this and it worked.
Maybe you can tell me where I could go to read more about how to use ubuntu - from the perspective of someone who has never used a PC.
Also, why is it that ubuntu doesn't have viruses?

What is the terminal and do I have to type in the long command lines anytime I want to install something?

---

### Post by yetiman64 on 2012-03-16
> **jones27557 said:**
> Thanks yetiman.  I did this and it worked.
Maybe you can tell me where I could go to read more about how to use ubuntu - from the perspective of someone who has never used a PC.
Also, why is it that ubuntu doesn't have viruses?

What is the terminal and do I have to type in the long command lines anytime I want to install something?
Good to hear it worked.

Personally I learnt Ubuntu via googling, I have seen beginner guide links posted here before, hopefully someone else will be familiar with them and post them here for you. I never actually used any beginner guides as I was fairly comfortable on computers after about 17 years on Windows.

There are viruses/malware for Linux, though none exist "in the wild" as it is a very robust security model in use. File/folder ownership/permissions are used to very effectively separate the user and root user. Hence if anything does get in it is usually restricted to the users home folder (which in itself is important of course, but the system itself can't be taken down as easily).

Always be very careful not to raise privileges with sudo or operate as root, real problems can be introduced if do so without understanding what is happening. BTW you had to raise privileges to install audacity then, but you did so specifically for the apt-get install command only not for all processes that you are running.

Never download and install directly off the net if there is a version in the repositories, those versions have been very carefully checked. Also I would recommend the use of a script blocker in your browser as there is cross platform malware that can do damage to your system. Viruses aren't a worry if you follow the advice in the link below, it covers not only viruses but general system security concerns for Ubuntu:

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)
[B]
No you don't have to use the terminal[/B], the Ubuntu Software Center is better for beginners, search for the word software in dash to access it. Giving a terminal command is far more convenient/quicker on a forum like this for helpers than having to explain steps. This comment does not just refer to installing software but is for all types of assistance.

Cheers, yetiman64

---

### Post by Helen McCall on 2012-03-18
If you are looking for the non-free packages in Ubuntu, then activate the Medibuntu repository in synaptic and then search for mp3 and you will get a whole selection of packages and libraries.

Audacity is really for editing music files rather than for playing collections of mp3s. Try one of the many music players such as the default banshee music player which will allow you to setup playlists etc with your colleciton of mp3s.

---

### Post by jones27557 on 2012-04-20
Thanks for all the replies.  I use audacity because I record all my banjo lessons.  audacity allows me to cut out all the unimportant crap and leave just the lesson.  I usually play them back on the banshee thing, or burn them to a CD for playback on a Cd player.

---

### Post by dwuorinen on 2012-05-16
i just started on Lbuntu and using audaxity  then ardour, I am using Mobile pre usb as and interface to plug in guitar and mics to, but when I go to preferences to designate them to record and playback, it lists several and I dont know what to select to record and playback.

any help pleaseeeee???????????

---

### Post by loklaan on 2012-05-16
> **dwuorinen said:**
> i just started on Lbuntu and using audaxity  then ardour, I am using Mobile pre usb as and interface to plug in guitar and mics to, but when I go to preferences to designate them to record and playback, it lists several and I dont know what to select to record and playback.

any help pleaseeeee???????????
Have you tried any the interfaces / devices?

I doubt you will break anything by trying the listed recording devices. :P

---

