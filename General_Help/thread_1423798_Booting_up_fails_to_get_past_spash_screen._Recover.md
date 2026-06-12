---
title: "Booting up fails to get past spash screen. Recovery mode also does not work properly."
date: 2010-03-07
forum: General Help
---

### Post by Sync.Demon on 2010-03-07
Currently, when I run version 2.6.31-20.57 regularly it will show the splash screen by not go any further. Where it should change to a screen with the word "ubuntu," loading bar, and back ground with lighting, it is just a blank screen.

When I run version 2.6.31-20.57 with "quiet splash" replaced by "debug" I end up with (initramfs) where I should get USERNAME@LinuxBox in the command line interface.

When I run version 2.6.31-20.57 in recovery mode I end up with (initramfs) where I should get USERNAME@LinuxBox in the command line interface. Any files that I wrote to the file system to later read and share were not there. In fact, I did not even have my home directory anymore (I was a frustrated user). It also said something about /dev/sdb1 or something like that, but I could not document it... because I could not write to my file system.

Running the previous version I had available to me from the grub menu, 2.6.31-14.48, was very questionable. At times it would do the exact same thing as the newer kernel. Other times it would run properly. I have done many scenarios trying to figure out what I did differently when it ran properly as opposed to when it just initramfs'ed me, but I came up with nothing conclusive.

Normally if I run 2.6.31-14.48 in recovery mode, I have no problems. There was 1 time when it resulted in (initramfs), but so far it has been pretty reliable. I had to startx from 2.6.31-14.48 in recovery mode to actually get here...

Additional notes: I am currently running linux off of an external 500gb USB hard drive. I have not had any problems until today after I updated... and I did not really have problems with the update immediately when I updated.

Any help is appreciated... I do not really know how to further approach this situation or debug what could possibly be wrong with this infernally limited contraption known as a computer. So far I have just been more and more frustrated as I have came up with no answers as to why it is not working properly.


UPDATE:
After extensive reading... I somehow am now able to boot up and run the kernel without any issues. I have absolutely no idea what I did. After I ran "sudo update-initramfs -u", I know that the latest kernel started working in recovery mode (though there was also fsck or something like that ran at one point in the old kernel in recovery mode). At first the new kernel did not work regularly... but when I went in ready to combat it and figure out what the issues were... I guess it was afraid of me... Anyways, I'm rather sceptical about this problem being completely resolved because I am at a loss as to what happened... but for now I guess it is fixed.

---

