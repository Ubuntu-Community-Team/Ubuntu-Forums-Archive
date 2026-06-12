---
title: "Ubuntu n00b"
date: 2010-05-21
forum: General Help
---

### Post by fDurdenC on 2010-05-21
Hi all, I'm extremely new to linux I've been a mac user for 6 years but  recently purchased a new laptop that has windows 7 and immediately made  the switch to ubuntu 10.04 after reading very good things. Problem is I like  what I see very much but have no idea what the heck I'm doing and have  ran into some problems.

1 How do you delete programs that are  under the applications tab? I ask this because I downloaded songbird but  my 32 bit system cannot open it so its there but cannot be used. Also  how do you delete programs in general that you wont need?

2 How  do I go about downloading songbird for the 32 bit OS?

3 I have  tried to download the cpu vista meter but don't know how to install it  once I have the files to extract.

4 When I boot up this machine I  have the option to start up 4 different ubuntu OS' Ubuntu 2.6.32.22 and  2.6.32.21 plus their recovery modes. Question is did I screw something  up during the partition and if not what is the difference between them  and do I need both.

5 is there any way to access options  regarding the sensitivity of the mouse pad it seems to be only for a  hand held mouse

6 is there anyway to change the sounds played by  empathy when messages are sent? are there any alternatives better than  empathy?

7 I never partitioned a HDD before and was wondering if  it was a good idea to set equal amounts of memory for windows and  ubuntu. Also whats a safe way of giving more memory to a partition or  removing a partition all together?

Thats it for now. I've ran  commands through the terminal to get the cairo dock and that worked fine  along with a few other apps. I just need some guidance and the basic  idea of how to install and run apps...but so far its been fun. any help  would be great just dont use crazy terms and if you have any  recommendations for what i should install please let me know. Thanks

---

### Post by pmlxuser on 2010-05-21
[http://ubuntu-manual.org/](http://ubuntu-manual.org/)

read thw manual all the questions will be answered.

for songbird, go to  http:// getsongbird.com and dowload the right version

---

### Post by Sef on 2010-05-21
> 6.  are there any alternatives better than  empathy?

I prefer pidgin which is available from the Ubuntu Software Center.  (Applications > Ubuntu Software Center)

---

### Post by fDurdenC on 2010-05-22
I appreciate the help, but it hasnt gotten me anywhere. I dont understand the terminology all that well.

My major question is how do I install things not from ubuntu software center? I've read a few things online but dont understand the terminology used like creating a usr/local/src directory.

if anyone can give me a step by step on the basics of installing that would be great. 

another question is how do i delete programs not installed through ubuntu software center?

If i use gparted to make my windows partition smaller is that safe?

and finally whats up with the 2 versions of ubuntu on the start up screen 2.6.32.22 and 2.6.32.21 is that normal and which one should I use?

ohh and another thing i dont know how i did it but the minimize expand and close icons on the tool bar switched from the left side to the right how do i change that?

---

### Post by jflaker on 2010-05-22
> **fDurdenC said:**
> I appreciate the help, but it hasnt gotten me anywhere. I dont understand the terminology all that well.

My major question is how do I install things not from ubuntu software center? I've read a few things online but dont understand the terminology used like creating a usr/local/src directory.

if anyone can give me a step by step on the basics of installing that would be great. 

another question is how do i delete programs not installed through ubuntu software center?

If i use gparted to make my windows partition smaller is that safe?

and finally whats up with the 2 versions of ubuntu on the start up screen 2.6.32.22 and 2.6.32.21 is that normal and which one should I use?

ohh and another thing i dont know how i did it but the minimize expand and close icons on the tool bar switched from the left side to the right how do i change that?

Go into the software center, click on INSTALLED PROGRAMS and remove what you like....Then to add stuff, go to GET SOFTWARE and install....

Change the windows controls
[http://ubuntuforums.org/showthread.php?p=9203080#post9203080](http://ubuntuforums.org/showthread.php?p=9203080#post9203080)

---

### Post by NTHQ on 2010-05-22
> **fDurdenC said:**
> I appreciate the help, but it hasnt gotten me anywhere. I dont understand the terminology all that well.

My major question is how do I install things not from ubuntu software center? I've read a few things online but dont understand the terminology used like creating a usr/local/src directory.

if anyone can give me a step by step on the basics of installing that would be great. 

another question is how do i delete programs not installed through ubuntu software center?

If i use gparted to make my windows partition smaller is that safe?

and finally whats up with the 2 versions of ubuntu on the start up screen 2.6.32.22 and 2.6.32.21 is that normal and which one should I use?

ohh and another thing i dont know how i did it but the minimize expand and close icons on the tool bar switched from the left side to the right how do i change that?
Don't worry about the 2 versions of Ubuntu. That's normal. If you want to remove one (I suggest 2.6.32.21) go to System -> Administration -> Synaptic Package Manager. After you enter your password, the enter linux-image in the search box. Find 2.6.32.21 and click the little square box to it's right and select "Mark for removal". Click Apply at the top and it will be gone.

Note: It is not always good practice to only keep one version of the kernel.

---

### Post by 2hot6ft2 on 2010-05-22
To move the buttons to the right

The best method is explained here along with more info. about the move.
[Known Lucid Lynx issues/bugs with workarounds]("http://ubuntuforums.org/showthread.php?t=1469475")
> **philinux said:**
> 
**[COLOR="DarkRed"]Minimize, Maximize and Close button placement.[/COLOR]**
A decision has been taken to move the placement to the left. Mark Shuttleworth explained that this was because "something" is going to be placed in the right hand area in the next release. Moving the buttons now would help enable this change.
**[Update ][http://www.markshuttleworth.com/archives/333](http://www.markshuttleworth.com/archives/333)**

The buttons are in the old location on all default themes apart from Ambiance,Radiance and Dust, If you still want the Ambiance ,Radiance or Dust theme but with buttons on the right, choose one of those other themes and use the Customize button to achieve what you want. e.g.
1. System > Preferences > Appearance
2. Select the theme icon "New Wave"
3. Click the button "Customize.."
4. Select tab "Controls" and select "Ambiance"
5. Select tab "Window border" and select "Ambiance"
6. Select tab "Icons" and scroll down and select "Ubuntu-mono-dark"
7. Select "Save Theme" to your choice.
**Using gconf-editor is not the right approach as this could bork future themes. This change makes it easier for themes to do interesting things with window borders.  Unfortunately, if the wrong approach spreads, they won't be able to do that.**

You should resize the windows partition from inside windows to be safe.

And you should keep the 2 most recent kernels that way if the newest one doesn't work right for some reason you have a working one to fall back to.
:popcorn:

---

### Post by themusicalduck on 2010-05-22
For installing programs that are not in the Software Centre, always pick .deb files. You can double click them and install the program like you would with a Windows exe.

Another way of installing software is by adding PPAs, which will keep the software updated automatically but it isn't quite as easy as using a deb.

You could get a songbird deb from here - [http://skyzim.com/songbird-1-4-3-installer/](http://skyzim.com/songbird-1-4-3-installer/)

Or if you want, add the GetDeb ppa and install it through there - [http://www.getdeb.net/updates/ubuntu/10.04/](http://www.getdeb.net/updates/ubuntu/10.04/) [http://www.getdeb.net/app/Songbird](http://www.getdeb.net/app/Songbird)

Also, I definitely recommend looking at [http://www.ubuntu-manual.org](http://www.ubuntu-manual.org) it explains all of this really well.

[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/) Is another good piece of software. It will make it easy to remove the extra kernels that clutter up your boot menu if you want.

---

### Post by bashphoenux on 2010-05-22
the 2.6.32.22 is the latest kernel and the other one is the default kernel that was installed in the begining, basically you can remove the old kernel option from the list.
[link]("http://ubuntuguide.org/wiki/Ubuntu:Lucid#GRUB_boot_manager_settings")
to get you started.

---

### Post by 3rdalbum on 2010-05-22
> **fDurdenC said:**
> I appreciate the help, but it hasnt gotten me anywhere. I dont understand the terminology all that well.

My major question is how do I install things not from ubuntu software center? I've read a few things online but dont understand the terminology used like creating a usr/local/src directory.

On Ubuntu, it's advisable to look on Google for a "repository" or a "PPA" that contains the software you want (for instance: go to Google and search for "programname PPA"). You can then tell your computer where this repository is, and then you can use Ubuntu Software Center or Synaptic Package Manager to install the software and keep it up-to-date.

There's always a page that tells you a particular line to copy and paste into the System > Administration > Software Sources program to add the repository or the PPA.

Songbird is no longer made for Linux, so forget about this.

If you're being told to create a /usr/local/src directory or something like this, then what you've downloaded is merely the source code for the program. The source code would need to be compiled. This stuff is not for new users, so don't try it until you have more confidence; there should be enough in the Ubuntu repositories, and in third-party PPAs, to last you a long time.

> another question is how do i delete programs not installed through ubuntu software center?

If you installed them from a .deb package or from Synaptic Package Manager, then you can remove them using Synaptic Package Manager. If you installed them in some other way, then you need to follow whatever instructions are given with the program.

> If i use gparted to make my windows partition smaller is that safe?

Reasonably safe, but remember to back up your data first. No partitioning operation is 100% safe to existing data. And it would also be a good idea to defragment the Windows partition.

> and finally whats up with the 2 versions of ubuntu on the start up screen 2.6.32.22 and 2.6.32.21 is that normal and which one should I use?

That's normal. You've obviously received a new version of the Linux kernel through the Update Manager system. Just boot into the latest version (the default entry, I believe).

> ohh and another thing i dont know how i did it but the minimize expand and close icons on the tool bar switched from the left side to the right how do i change that?

You probably changed theme. Only two of the Ubuntu themes have the buttons on the left. What you can do is switch back to the default Ubuntu theme ("Ambiance") in the Appearance program, and then click on "Customise" and change each individual component of the theme to match whatever you want. This way, you'll keep the buttons on the left.

---

### Post by 3rdalbum on 2010-05-22
> **2hot6ft2 said:**
> To move the buttons to the right

He didn't ask how to move the buttons to the right, he asked how to move them back to the left :-)

---

### Post by fDurdenC on 2010-05-23
> **3rdalbum said:**
> On Ubuntu, it's advisable to look on Google for a "repository" or a "PPA" that contains the software you want (for instance: go to Google and search for "programname PPA"). You can then tell your computer where this repository is, and then you can use Ubuntu Software Center or Synaptic Package Manager to install the software and keep it up-to-date.

There's always a page that tells you a particular line to copy and paste into the System > Administration > Software Sources program to add the repository or the PPA.

Songbird is no longer made for Linux, so forget about this.

If you're being told to create a /usr/local/src directory or something like this, then what you've downloaded is merely the source code for the program. The source code would need to be compiled. This stuff is not for new users, so don't try it until you have more confidence; there should be enough in the Ubuntu repositories, and in third-party PPAs, to last you a long time.



If you installed them from a .deb package or from Synaptic Package Manager, then you can remove them using Synaptic Package Manager. If you installed them in some other way, then you need to follow whatever instructions are given with the program.



Reasonably safe, but remember to back up your data first. No partitioning operation is 100% safe to existing data. And it would also be a good idea to defragment the Windows partition.



That's normal. You've obviously received a new version of the Linux kernel through the Update Manager system. Just boot into the latest version (the default entry, I believe).



You probably changed theme. Only two of the Ubuntu themes have the buttons on the left. What you can do is switch back to the default Ubuntu theme ("Ambiance") in the Appearance program, and then click on "Customise" and change each individual component of the theme to match whatever you want. This way, you'll keep the buttons on the left.

Thanks a lot thats some good info i will try the ppa, I was able to get songbird by following that persons link and it works well.

Thanks to everyone this really helped me out! one more question for now. Say Id like to imports files and or programs from my windows os specifically games, would i have to make those files shared files from within windows and im under the impression i can get those games from wine or is this not possible?

---

### Post by fDurdenC on 2010-05-23
how can i install this after i download it?

[http://gnome-look.org/content/show.php/CPU+Meter+Screenlet+vista'ish+look?content=64599](http://gnome-look.org/content/show.php/CPU+Meter+Screenlet+vista'ish+look?content=64599)

---

### Post by themusicalduck on 2010-05-23
> **fDurdenC said:**
> Thanks to everyone this really helped me out! one more question for now. Say Id like to imports files and or programs from my windows os specifically games, would i have to make those files shared files from within windows and im under the impression i can get those games from wine or is this not possible?

Wine is a way to run Windows applications on Linux. If you've already installed it, you can generally just run .exe files (if you set it in properties, right click an exe file, go to Properties, Open With). You also need to set the file to be executable in Permissions tab.
The best way is to install an app in the same way as Windows with the setup files, but you could try to run the already installed files on the Windows partition. Or copy it to your homespace if you like. (Most wine files are kept in /home/name/.wine/drive_c/Program Files/) but you'd have to add launchers manually using ```
wine /path/to/exe
``` as the command. If you install with the setup files it makes launchers automatically.

I'd recommend using wine1.2 rather than wine as it's more developed. Both are in the software centre.

Also look at [http://appdb.winehq.org/](http://appdb.winehq.org/) and search for your application to see if it's compatible or if there are any tweaks to do first.

> how can i install this after i download it?

[http://gnome-look.org/content/show.p...?content=64599](http://gnome-look.org/content/show.p...?content=64599)
First install screenlets from the Software Centre. Run it from Applications > Accessories > Screenlets and click the Install button then select the file you downloaded.

---

### Post by fDurdenC on 2010-05-28
every so often when i boot up and open a window theres no tool bar above any of my windows. I usually get them back after i restart a few times. Any ideas on how to fix this bug?

---

