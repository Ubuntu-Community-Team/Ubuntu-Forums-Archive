---
title: "webcam doesn't work from cron when not logged on."
date: 2011-12-26
forum: General Help
---

### Post by John Coulthard on 2011-12-26
I use a program called webcam to capture a picture from my webcam and upload it to my website on an hourly basis. Somewhere along the upgrade line to 11.04 and 11.10 it stopped working when I was not logged on. I finally spent a morning chasing down this problem and wanted to share it, hopefully helping someone else avoid a frustrating morning. First I present the solution and then document the false leads. 

The cron job couldn't be simpler "webcam". The program is controlled by the file .webcamrc in my home directory. 

Solution: The account the program is run from must be a member of the group "video". I did this using the Users and Groups gui, which was present on my 11.04 machine. I had to install it on the 11.10 system. I installed "gnome-system-tools" using the Ubuntu Software Centre. 

Solving the problem: Examining syslog gave me two messages; "info (No MTA installed, discarding output)" and "Error (grandchild #1818 failed with exit satus 1)". The first one is not an error message and was simply letting me know what I already knew - that I wasn't intercepting the output yet. It disappeared when I finally managed to redirect the output to a file as shown below. The second just appears to be a red herring. It still occurs when webcam runs when I am not logged on and what it means I am not sure, but the program works. 

The problem was to redirect the webcam output to a file and the common advice was to use the syntax "&>" ah so... "webcam &> webcamoutput". This works fine from a terminal but simply did not when the program was running under cron. Along the way I ended up chasing down a couple of blind alleys. One was that the full path must be supplied for all file names (it made no difference). Another was that no period "." could be present in a file name (the default control file is .webcamrc - but it made no difference). I finally came across a comment in the forums that the syntax "&>" is a bash extension and will not work under cron. the correct syntax is "webcam 2> webcamoutput" and  I was off to the races. 

The error message when I was not logged on was "open /dev/video0: Permission denied." When I go in and check the permissions for /dev/video0 it is read write "root" and group "video". From there the solution fell out quite quickly. I'm not really sure why it worked when I was logged on and not a member of the group "video". 

I hope this is helpful to someone.

---

