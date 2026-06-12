---
title: "Failing at Getting My Feet Wet..."
date: 2010-03-19
forum: General Help
---

### Post by {Synapse} on 2010-03-19
I recently made the switch over from Windows (around a month ago) and definitely enjoy the change of scenery from the all-too-familiar Windows XP setup. Yet I've hit a wall. I've learned the basic commands and such in Terminal, yet I don't seem to be able to continue to *learn* more. In Windows, things seemed to sort of manifest themselves, like mounting ISOs to virtual drives and general troubleshooting, in a fairly straightforward way. But I'm too unfamiliar with Linux with really have that base of knowledge to go off of. Does anyone have any recommendations for things that would not only be beneficial and fun to attempt, but also would help me learn more about this OS and its intricacies?

---

### Post by jobix on 2010-03-19
One way to learn "more" would be search the web for "linux tutorial" or similar. A better way to be actually do something and learn in the process of doing. That way you won't forget what you learn.

Just an example of a very simple project you could do:
1 - publish a photo to your blogger/facebook/whatever account.

This would probably involve the following steps:
- get a picture from your camera which means
-- connect your camera to your linux machine via usb cable.
    At this point, depending on your set-up, something might pop up, e.g., F-Spot. You can use that to transfer a pic. Otherwise, you can do it from the command line in a terminal which would involve figuring out where the camera filesystem is mounted (typically in the /media directory) and using the "cp" command to copy it over to a directory which you made using the "mkdir" command.
-- now, you want to see what the pic looks like. So you use the "eog" command.
-- then, you decide to see how large the pic is and you use "ls -l".
-- you see it's 10MB and decide it's too big. What to do? Voila! "gimp" to the rescue. You open up "gimp" from the command line and edit the picture.
-- after everything looks good, you publish it.
-- then you decide you want to publish a few which you then proceed to do.
-- having done that, you decide that you want to save space and compress these files. So you use the "gzip" command.
-- but you're not satisfied with having a .gz file for each pic. What you really want is an archive folder a la Windows. So, you use the "tar' command to create an archive file.
-- and so on...

Every time you run into a problem, you have the internet and this forum to try to get your answers. For example, you might not know that "tar" exists, but you can always pose a query "how to archive files in linux" and soon enough you'll meet tar.

A couple of other simple projects off of the top of my head:
- convert your CD collection to a mp3 collection on your hard drive
- extract your favorite tune from one of your collections and use it as a ring tone for your phone

---

### Post by jobix on 2010-03-19
.

---

### Post by Greenwidth on 2010-03-19
Not massively useful but how about setting up a conky script for your desktop?
Inspiration:
[http://ubuntuforums.org/showthread.php?t=281865&page=1227](http://ubuntuforums.org/showthread.php?t=281865&page=1227)

---

### Post by Iowan on 2010-03-19
Have you read the Stickies at the top of the [Absolute Beginner Talk]("http://ubuntuforums.org/forumdisplay.php?f=326") forum? 
I learn best by doing - pick a project (like a server) and try to set it up. I also like a safety net - so I usually have a "development machine" to work on - then I still have internet access on a different machine when I need to search for answers.

---

### Post by g4ry.l33 on 2010-03-19
Have you tried shell scripting? It's fun and a good way to put the
commands you've learned to good use. You'll learn some new commands
as well.

[http://bash.cyberciti.biz/guide/Main_Page]("http://bash.cyberciti.biz/guide/Main_Page")

---

### Post by {Synapse} on 2010-03-20
jobix: You're right: linux tutorials only can do so much. That was sort of my problem. I was just reading seemingly endless collections of tutorials and it did a better job of numbing my brain rather than inform me. I never was one to just learn something because I read it, which was why I was wondering what kind of "projects" were of beginner level. I managed to install uTorrent and Skype through Wine, but that was purely through the GUI and gave me this sick feeling of cheating, since I basically ignored the command line and didn't really learn anything from the experience. I didn't even realize you could upload pictures to Facebook purely through terminal; I guess I didn't give Linux enough credit.

Greenwidth: ......Conky script? Would it be dumb to ask what that is....

Iowan: I hadn't; I had no idea this forum was so helpful and user-friendly. That probably would have been a good place to start. So do I, that was sort of my question. I just didn't know what would be a useful, yet fairly beginner task I could attempt. I have my Windows machine next to my Ubuntu laptop. I was entirely too afraid to just do a clean reformat on my primary machine xD

g4ry.133: I have tried out shell scripting and know several simple commands, but haven't really had much need to put it to use, partly due to the tried-and-true GUI Ubuntu has to offer, partly due to simply not knowing when to use what command in what way. I've found cheat sheets and tutorials and such, yet a project of some kind would be much better than just reading web pages.


Thank you all for your fast and informative responses! After coming from the harsh, unfriendly world of Windows, such an amazing and friendly forum base is like a breath of fresh air!

---

