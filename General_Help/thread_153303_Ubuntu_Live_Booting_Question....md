---
title: "Ubuntu Live Booting Question..."
date: 2006-03-31
forum: General Help
---

### Post by spiralstarez on 2006-03-31
So I'm a Windows XP user but a ton of open source stuff and a growing distaste of "The Big Fish" has lead me to try out Ubuntu.

I'm booting from a live CD of 5.10, and it seems to work okay and then I freeze at this prompt:

[dr-dos]A:/>

And I don't know what to do.  Help is much appreciated and thanked for in advance.

Thanks,

Jason

---

### Post by localzuk on 2006-03-31
That looks like a Windows/Dos prompt rather than a Linux one? How are you trying to boot the cd? Did you download the iso from the site and burn it to disk?

---

### Post by spiralstarez on 2006-03-31
Yeah, I first downloaded it and put it on a CD which didn't boot.  I then realized that I needed to burn a bootable disc so I did that.

I just reset the computer, leave the disc in it appears to be working.  on the last screen there are some options I don't understand in a box, stuff like \abc, \def (not the real ones but just as an example) etc.

and then underneath I have that prompt.

---

### Post by Ramses de Norre on 2006-03-31
That definitely isn't the default linux prompt..
What screens do you get before it? Should be blue screens with progress bars and it should check then some hardware and initialize some apps.

---

### Post by spiralstarez on 2006-03-31
Ok, I went back and tried it again.  It obviously isn't trying to fire up Ubuntu.  I get 

'starting Caldera DR-DOS'

Some other stuff I thought might be pertinent:  

DeviceName MSCD001

and at the last part it says:

'Protected Mode Services'

I don't know anything really about hardware, or what really to look for, but this only happens when I have the CD in, so definitely caused by the boot CD.  It's as though there's something rerouting to DOS when it sees the boot CD

I made the boot CD with Nero Express if that matters.  I just chose 'create bootable disc' and put all the files on it.

---

### Post by spiralstarez on 2006-03-31
I thought it might also be helpful to give my system info...

I'm on an Athlon 64 and have FastTrack Controller (not that I know what any of this means).  I think also it uses IDE instead of RAID?  

Anyway, I don't understand any of that stuff, but I thought it might help determine what's going on for those who are more knowledgable than I.

---

### Post by localzuk on 2006-04-01
What do you mean by 'created bootable cd' did you download the ISO and burn it to disc (command such as 'burn cd-image to disc' in nero)? Copying files will not work - you have to use the ISO provided.

---

### Post by 3rdalbum on 2006-04-01
When you burn the disc, you must use the Disc Image function of your burning software. Select the .iso file, and burn. It should work okay now.

The data in the ISO file is more than just the files you can see in Windows.

I think the "bootable" function you described has actually installed a kind of free DOS that runs on the CD.

---

### Post by spiralstarez on 2006-04-01
Great thanks for the help everyone.  I don't feel the brightest as it was only that I couldn't burn the disc properly!

I'm typing this in from Ubuntu right now.  So far it seems pretty cool - though I can't seem to put my resolution on my primary higher than 1024X768, and extending to my second?  I have no idea where to start...

But I'm sure I'll learn.

Thanks again.

J

---

