---
title: "Jaunty: how to low-level format 720k floppy"
date: 2011-12-19
forum: General Help
---

### Post by stlu on 2011-12-19
I had to figure this out from bits and pieces, so I'm putting this here as a complete solution for anyone else.

Situation:  I was running badblocks checks on some floppies I had acquired, and got a strange result from badblocks with a several 720k floppy disks:

> 
**#badblocks -sv /dev/fd0**
[B]checking blocks 0 to 3
...
Pass completed, 4 bad blocks found.
[/B]Other 720k floppies went through the test checking all 720 blocks with success - save for a couple that did have bad blocks.

I booted a win98 startup disk and was able to format these 4-block floppies.  After which they worked fine with badblocks and then filesystem creation.  So I concluded that badblocks sees floppies (at least the 720k ones) as having 4 blocks until they are low-level formatted.

I then searched around picking up what I could, until I found out what I need to do.  Ultimately I found that the correct utility included with Ubuntu Jaunty is "fdformat".  However, the command does not work on a 720k floppy when it is present in /dev/fd0 and has not been low-level formated.  

Other instructions said to use "fdformat /dev/fd0u720" but that device doesn't exist in default jaunty.  It has to be created.

Here is my successful approach:


[LIST=1]
[*](for Jaunty, i386)Download fdutils from [https://launchpad.net/ubuntu/jaunty/i386/fdutils/5.5-20060227-3](https://launchpad.net/ubuntu/jaunty/i386/fdutils/5.5-20060227-3)
[*]Double-click the downloaded fdutils package to install it.
[*]In the terminal, run the newly installed script (caps) "sudo MAKEFLOPPIES"
[*]the /dev/ directory will now contain fd0u720
[*]Run the low-level formatter - "sudo fdformat /dev/fd0u720"
[/LIST]

Hope this helps!

EDIT:

Jaunty badblocks will also report "0 to 3" when checking unformatted 1.44MB floppy disks.  The above steps will work, using the device /dev/fd0u1440 instead.

The terminal command is "sudo apt-get install fdutils" which completes steps 1 and 2.

---

