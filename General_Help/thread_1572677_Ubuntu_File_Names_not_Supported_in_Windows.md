---
title: "Ubuntu File Names not Supported in Windows?"
date: 2010-09-11
forum: General Help
---

### Post by zukafute on 2010-09-11
Hi,

I dual-boot Windows and Ubuntu 10.04. I used Songbird to manage my media files. It renames the files using the default character encoding for Ubuntu, which for me is UTF-8. I did not notice it until i switched into Windows one day to sync my zune, and found out that filenames with ":" or "?" are not recognized by windows (I get an error). Is there some way that i can switch my default ubuntu encoding to be compatible with windows file naming? Please help :(

---

### Post by Silent Warrior on 2010-09-11
Just... don't use : or ? in the filenames. I think Windows is very specifically against that kind of thing, so it should be much easier to just rename the files than doing things with the encoding.
For the record, though, I think Winamp's supposed to accept UTF-8... It might take some juggling even there, and the UTF-support's only valid for the metadata, but still.

---

### Post by WorMzy on 2010-09-11
Windows Explorer just doesn't like the following characters: \ / : ? * " > < |

Just avoid using them in filenames and they will be cross-compatible.

---

### Post by zukafute on 2010-09-11
I understand all that, thank you for your input.

But still.. i have a HUGE music library, and songbird already renamed most of the songs.. so none of them are windows-compatible anymore. I tried the convmv but i got lost on the way. Like is there anyway to convert all the special characters to underscores without having to rename them one by one? And is there anyway i can change the default encoding to not do that anymore? :???:

---

### Post by zukafute on 2010-09-11
Im soon due to ditch windows 98% (zune = no compatibility). But this is the only problem I am having that is blocking me.

---

### Post by WorMzy on 2010-09-11
I don't use songbird, but I expect there's some option in the preferences to disallow special characters from filenames, it's a multi-platform application after all, so it must be able to rename files for use on Windows OS'. Have a poke around and see what options there are.

---

### Post by jamesisin on 2010-09-11
I run a Windows share on my local network for my music library (mostly Ubuntu machines, but Windows/Samba is easy to work with).  I have the same problem with : ? &c.  In my case, Samba still shows the files but with weird character strings for names (0asv32.flac or some such).  Then I know to find that file/folder and fix its name.

I rip using Grip which removes many (perhaps too many) potentially offensive characters from the file/folder names (but not from the tags):

[http://www.soundunreason.com/InkWell/?p=1220](http://www.soundunreason.com/InkWell/?p=1220)

So it's only files/folders that I created prior to using Grip that are problematic.  When I download files and attempt to move them to the server (across Samba) they error out and I know immediately to fix the file/folder name.

Maybe that's imperfect but it seems to work well enough for me.

---

### Post by jamesisin on 2010-09-11
Oh, also, you might check to see if you can run RockBox on your Zune.  I run it on my iPod and love it.  Full FLAC/ogg support.

[http://www.rockbox.org/](http://www.rockbox.org/)

---

### Post by zukafute on 2010-09-11
@jamesisin,

Rockbox doesnt work, and I'm a little scared of using grip.. but thanks for the recomendations! :razz:

I  just want to be able to *not* use those special characters in filenames  across the OS, or find a way to rename the files that have been  affected.

---

### Post by zukafute on 2010-09-11
Or, can someone recommend a media managing software for ubuntu? 

File folder, Artist, Trackname.mp3

:( :)

---

### Post by dcstar on 2010-09-11
> **zukafute said:**
> Hi,

I dual-boot Windows and Ubuntu 10.04. I used Songbird to manage my media files. It renames the files using the default character encoding for Ubuntu, which for me is UTF-8. I did not notice it until i switched into Windows one day to sync my zune, and found out that filenames with ":" or "?" are not recognized by windows (I get an error). Is there some way that i can switch my default ubuntu encoding to be compatible with windows file naming? Please help :(

Windows filesystems are **different** from Linux filesystems and have **different** allowable characters.

Linux tools are generally designed for Linux systems and unless they **specifically** have settings to make their output compatible for other filesystems then they work fine in the environments that they are meant to work in.

There is no "encoding" to change because that is not the issue, the issue is trying to use **different** operating systems and expecting everything to work.

---

### Post by jamesisin on 2010-09-12
> **zukafute said:**
> Rockbox doesnt work, and I'm a little scared of using grip...

I  just want to be able to *not* use those special characters in filenames  across the OS, or find a way to rename the files that have been  affected.

If you follow the link I posted to my blog, you will find an article for using Grip which should give you all you need to be successful with it.  Then your problem of the wayward characters will be solved.  You enter the track names as you want them in the tags (which is to say properly) and Grip only uses so-called safe characters in the file names themselves.

(I use Rhythmbox for music library management, but I don't use it for ripping in part because it doesn't strip unsafe characters from file names.)

---

### Post by dcstar on 2010-09-12
> **jamesisin said:**
> If you follow the link I posted to my blog, you will find an article for using Grip which should give you all you need to be successful with it.  Then your problem of the wayward characters will be solved.  You enter the track names as you want them in the tags (which is to say properly) and Grip only uses so-called safe characters in the file names themselves.
........

I also use Grip, and it is a pity that the Gnome developers have deprecated it in favour of other CD ripping programs.

---

### Post by jamesisin on 2010-09-12
Yeah, David.  Super bummed about that.  I did find a repo though:

[http://www.soundunreason.com/InkWell/?p=1440](http://www.soundunreason.com/InkWell/?p=1440)

---

### Post by Ubunthree on 2010-09-12
I don't know whether this will help here or not, but it might be useful for someone else anyway:

The Thunar file manager (install via Synaptic) has a nice bulk-rename function which you might be able to use to strip the problematic characters out of the filenames. You can select any number of files or folders and hit "Rename," and you can add sequential numbers, insert characters, search and replace, and convert between upper- and lowercase. A two-column display shows before-and-after views so you can see what is going to happen before you hit "Rename files." Maybe you could select a group of files, add numbers to them to avoid duplicate filenames, replace the illegal characters with usable ones, and convert to all lowercase. It would take several steps, but it might at least give you filenames that Windows will accept, and better than doing each individual file manually.

---

### Post by Nythain on 2010-09-12
> **Ubunthree said:**
> I don't know whether this will help here or not, but it might be useful for someone else anyway:

The Thunar file manager (install via Synaptic) has a nice bulk-rename function which you might be able to use to strip the problematic characters out of the filenames. You can select any number of files or folders and hit "Rename," and you can add sequential numbers, insert characters, search and replace, and convert between upper- and lowercase. A two-column display shows before-and-after views so you can see what is going to happen before you hit "Rename files." Maybe you could select a group of files, add numbers to them to avoid duplicate filenames, replace the illegal characters with usable ones, and convert to all lowercase. It would take several steps, but it might at least give you filenames that Windows will accept, and better than doing each individual file manually.
I second this idea, like said, its a few steps, might take a little time on a large collection of files, but it's probably the most simple way to bulk rename and get rid of windows illegal characters.

another option would be the command line tool "rename" with a little regex magic (wich im no good at, but google is your friend)... but i would probably try the thunar route first

---

