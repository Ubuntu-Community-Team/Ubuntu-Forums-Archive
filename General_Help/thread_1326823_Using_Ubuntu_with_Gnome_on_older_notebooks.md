---
title: "Using Ubuntu with Gnome on older notebooks"
date: 2009-11-14
forum: General Help
---

### Post by steelcommuter on 2009-11-14
I've inherited an older barebones Thinkpad with a 1.5 GHz processor and 256 MB ram, and it runs the OEM Windows XP well.  I have found that Ubuntu runs slow on it, unless I use a variant like Crunchbang that uses a lightweight windowmanager.  Vector Linux Lite runs well on it, using icewm.

This laptop seems like an ideal candidate for students to use in the library at the school I teach at, and I would like to gather together additional older laptops around our district and put together a budget set of mobile computers for student research projects at the library.  Ideally, I'd like to install an easy-to-use linux distribution that could run Firefox and OpenOffice.  Ideally, it would use Gnome, which has a very simple and straightforward appearance.  I think some of the leaner windowmanagers are a bit stark in presentation or confusing.  For instance, Crunchbang is a great Ubuntu-spinoff but frankly Openbox may confound students.

I can try using XP for these systems, but I would prefer Linux for administration purposes.  Unfortunately, whereas XP is a 7 or 8 years old and is still supported by MS, older versions of Ubuntu and other distros tend to be abandoned after a few years.  Additionally, Ubuntu does not make major upgrades of software within a particular version, so Firefox 2.x will not be upgraded to 3.0 or 3.5.  

Is there any way to run a version of Ubuntu on older notebooks that can be optimized to run as fast as XP, while still using Gnome?  Or do I need to look at another distro that is less resource intensive?  Ubuntu appeals to me because it is widely used, offers a wide variety of software, and has regular updates.  Unfortunately, most Gnome-centric distributions such as Ubuntu seem to run slowly on older hardware (unless you switch to Fluxbox/icewm and their kin.

Any helpful responses are appreciated.

---

### Post by williejones on 2009-11-14
I am running Ubuntu on a 1998 Compaq Pressiro desktop.
900 processer, 356 ram, using a USB Netgear wireless
connection.  Runs good.  I have run 9.04 and 9.10.

---

### Post by mikewhatever on 2009-11-14
You can make Ubuntu/Gnome run a bit faster by disabling some of the unneeded startup programs and services, but, nevertheless, Gnome isn't a speed demon by design. Xubuntu/XFCE is somewhat lighter and rather well supported, but no speed demon either. I've heard Debian with Gnome uses a lot less resources, but never actually tried it.
You can keep Firefox uptodate with Ubuntuzilla.
[http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Welcome_to_Ubuntuzilla](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Welcome_to_Ubuntuzilla)

---

### Post by marshag63 on 2009-11-14
I have a Dell Inspiron 6000 (700 MHz with 512 MB Ram).  I have both Linux Mint 6 and crunchbang installed.  By turning off things like Gnome-Do and Compiz, and tweaking Firefox and OpenOffice, it can run decently without problems. Gnome-Do and Compiz are awesome if you have a newer machine, but better to go without on our older lappys.   I do have a Firefox extension for downloading videos and that can start to bog things down, as is expected when doing that kind of thing.


I totally understand where you are coming from talking about crunchbang (an awesome distro for someone with a little more experience) and gnome - gnome is more logical to someone more familiar with windows.

Saw a great article very recently in a Linux magazine about tweaking gnome, Firefox and openoffice.

Good luck with your project!

MarshaG.

---

### Post by steelcommuter on 2009-11-15
> **marshag63 said:**
> I have a Dell Inspiron 6000 (700 MHz with 512 MB Ram).  I have both Linux Mint 6 and crunchbang installed.  By turning off things like Gnome-Do and Compiz, and tweaking Firefox and OpenOffice, it can run decently without problems.

Saw a great article very recently in a Linux magazine about tweaking gnome, Firefox and openoffice.

Good luck with your project!

MarshaG.

I'll have to find something then about optimizing Gnome, then.  Thanks for the suggestion.  The low RAM is definitely the biggest problem for me.

---

### Post by marshag63 on 2009-11-15
steelcommuter, I found my ram on e-bay for about $20.  

Here's some tips for OpenOffice:
[http://www.zolved.com/synapse/view_content/28209/How_to_make_OpenOffice_run_faster_in_Ubuntu](http://www.zolved.com/synapse/view_content/28209/How_to_make_OpenOffice_run_faster_in_Ubuntu)

Try disabling things like Remote Desktop, Visual Assistance, Bluetooth Manager.  Also, change how often the update manager checks for updates - I changed mine to once a day and increased the wait time for startup of update manager to a matter of minutes so that other apps have time to get going.  

They say Firefox 3.5 runs faster than any previous version, but you could also try swiftfox.  

What sorts of things will these students be needing to do besides using openoffice and a web browser?  Will they be working with video?  Will they be writing documents?  Will they be managing projects or databases?   Knowing more specific purpose, we might be able to give better tips.  You will have to find the acceptable balance between speed and ease of use and usefulness.  

I had an old Dell running at 600 MHz that I put Mint Fluxbox on and ran conky with all the keyboard shortcuts for the things they probably would use the most - starting firefox was Windows key + W, file manager was windows key + f, etc. I donated that computer to a local thrift store - they liked it! - but I digress.

Let us know what you will be needing to do and maybe we can suggest some things.

MarshaG.

---

### Post by steelcommuter on 2009-11-15
> **marshag63 said:**
> steelcommuter, I found my ram on e-bay for about $20.  

Here's some tips for OpenOffice:
[http://www.zolved.com/synapse/view_content/28209/How_to_make_OpenOffice_run_faster_in_Ubuntu](http://www.zolved.com/synapse/view_content/28209/How_to_make_OpenOffice_run_faster_in_Ubuntu)



What sorts of things will these students be needing to do besides using openoffice and a web browser?  Will they be working with video?  Will they be writing documents?  Will they be managing projects or databases?   Knowing more specific purpose, we might be able to give better tips.  You will have to find the acceptable balance between speed and ease of use and usefulness.  

I had an old Dell running at 600 MHz that I put Mint Fluxbox on and ran conky with all the keyboard shortcuts for the things they probably would use the most - starting firefox was Windows key + W, file manager was windows key + f, etc. I donated that computer to a local thrift store - they liked it! - but I digress.

Let us know what you will be needing to do and maybe we can suggest some things.

MarshaG.

Good questions.  I can see them wanting to watch Flash video for researching, but no video or audio editing.  They will want to create simple spreadsheets, presentations, and write essays.  Additionally, they will have internet access and will be using Firefox.

Mint didn't have a Fluxbox edition for 7, just the XFce version which did not appear to be faster than Gnome when I tried it.  I know that XFCE is not really a "lightweight" windowmanager, although it impresses me.

Thanks for the link concerning OpenOffice, I'm sure it will prove useful.

The main goal for this project is to get our library a working mobile PC lab on an extremely tight budget while I start the process of writing applications for grants that will fund a more expensive mobile cart.  Windows XP has the advantage of running well on 6-7 year old hardware, since XP itself is older.  I can also install new programs on it.  Despite this, I would prefer to run an updated popular Linux distro like Ubuntu.  The existing student PCs in the library are 6.10? Edubuntu thin clients, and I would like to keep the computers all on the same distribution.

---

### Post by marshag63 on 2009-11-15
You will definitely want to stick with openoffice - the tweaks should help.

For firefox, if you scale back how many days of history it keeps, that will help. Also, instead of watching flash video over the internet, you can get the "Video Downloadhelper" plugin and download videos to the PC (this app is set to download to a folder named 'dwhelper' in the /home/USER directory, but that can be changed - no video lagging when you do it that way).  

I'm sure others will have suggestions helpful for college students - perhaps for tracking classwork, etc.  

Sounds like you may have to compromise a little bit of speed for ease of use -- remember that a live cd runs slower than an actual install.  I'm not sure what ubuntu defaults to for size of swap partition, but it should be at least twice the amount of ram in the computer, but I used to make mine even bigger - like 800 mb (ran the live cd the first time to setup the swap partition, then shutdown and restarted again to do the install..  You can save some time and space by skipping install of all the languages.

XFCE is nice!  

I know college kids like music - if you can convince them to use a console app like moc (music on console) their PCs' won't bog down.  I also just found a console app for pandora.com (and last.fm) - its called pianobar.

I also recently installed moonlight (like silverlight, but for linux) and also the firefox add-on "user agent switcher" for those websites that are IE-based.

BTW, you can shave a few second at bootup if you set your harddrive as the first boot drive (bypassing the cd-rom drive) and also disable the floppy drive.  Also, if feasible, set the user to autologin (make sure to keep administrator as a separate user, of course).

It will be interesting to hear what you find works best.

MarshaG.

---

### Post by mikewhatever on 2009-11-17
Just stumbled on this blog -> [http://andyduffell.com/techblog/?p=361](http://andyduffell.com/techblog/?p=361)
Thought the OP might be interested. The comments below are also useful.

---

### Post by mikewhatever on 2009-11-18
> **steelcommuter said:**
> .......................

Is there any way to run a version of Ubuntu on older notebooks that can be optimized to run as fast as XP, while still using Gnome?  Or do I need to look at another distro that is less resource intensive?  Ubuntu appeals to me because it is widely used, offers a wide variety of software, and has regular updates.  Unfortunately, most Gnome-centric distributions such as Ubuntu seem to run slowly on older hardware (unless you switch to Fluxbox/icewm and their kin.

Any helpful responses are appreciated.

What about the latest Fedora/Gnome? I really like its system requirements:

>   Processor and memory requirements for x86 Architectures

The following CPU specifications are stated in terms of Intel processors. Other processors, such as those from AMD, Cyrix, and VIA that are compatible with and equivalent to the following Intel processors, may also be used with Fedora.

Fedora 12 requires an Intel Pentium Pro or better processor, and is optimized for i686 and later processors.

    * Recommended for text-mode: 200 MHz Pentium Pro or better
    * Recommended for graphical: 400 MHz Pentium Pro or better
    * Minimum RAM for text-mode: 128MiB
    * Minimum RAM for graphical: 192MiB
    * Recommended RAM for graphical: 256MiB 

As a side note, I just got back from a neighbor's, after helping to reinstall an antivirus on their computer. The machine was a 5-6 year old desktop with 2Ghz Celron, 256MB of RAM and integrated graphics, running a legit copy of Windows XP SP2, but the performance was horrible. The computer was obviously short on RAM, as the page file was over 300MB full right after startup. It took about 10 minutes and several tries to uninstall the old antivirus, manipulating windows was extremely slow, with visual tearing and short periods of blanking out, and with desktop icons disappearing. What a treat.
It's been a while since I used such a machine, and now, I have serious doubts one could run XP with Firefox, Open Office and whatever security software on such limited resources.

---

### Post by steelcommuter on 2009-11-18
> **mikewhatever said:**
> What about the latest Fedora/Gnome? I really like its system requirements:



As a side note, I just got back from a neighbor's, after helping to reinstall an antivirus on their computer. The machine was a 5-6 year old desktop with 2Ghz Celron, 256MB of RAM and integrated graphics, running a legit copy of Windows XP SP2, but the performance was horrible. The computer was obviously short on RAM, as the page file was over 300MB full right after startup. It took about 10 minutes and several tries to uninstall the old antivirus, manipulating windows was extremely slow, with visual tearing and short periods of blanking out, and with desktop icons disappearing. What a treat.
It's been a while since I used such a machine, and now, I have serious doubts one could run XP with Firefox, Open Office and whatever security software on such limited resources.

Thanks for the link.  I am not too familiar with Windows XP, although I use it for various tasks at work.  I noticed that a new install of XP on the Thinkpad was fast enough to play video and run Open Office, but on another Thinkpad (the same exact model) with an older installation XP ran excruciatingly slow.  Your description matched my own experience.  I have NO idea why it would slow down so much, simply on boot-up and opening Office.  If anyone knows the specific details of this, please share if convenient.

I installed Ubuntu using the alternate ISO on one of the laptops today, and tomorrow I will start configuring it using the information included in the helpful links posted on the thread.

---

