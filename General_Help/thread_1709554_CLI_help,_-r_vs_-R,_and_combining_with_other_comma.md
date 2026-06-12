---
title: "CLI help, -r vs -R, and combining with other commands"
date: 2011-03-18
forum: General Help
---

### Post by kansasnoob on 2011-03-18
Many, many moons ago I was taught that it was best to amend commands such as "rm" with "-R" rather than "-r". I never asked why but I know if I'm using "rm" to remove a directory and I want to remove all of it's contents that "rm -R" just works.

Now, I tend to stick with the "old" until it no longer works with no question. For instance I stuck with "--purge remove" long after only "purge" became necessary. I'm old and stuck in my ways.

Anyway on to specifics. Let's say I want to backup and remove /boot/grub and all of it's contents, I'm used to running:

sudo mv /boot/grub /boot/grub_OLD
sudo rm -R /boot/grub

So, what is the difference if I use a lower case -r?

Further more I'd normally follow that by creating a new /boot/grub by running:

sudo mkdir /boot/grub

And then of course reinstalling the proper version of grub, but it now appears that I could just as easily run one command:

sudo cp -R /boot/grub /boot/grub_OLD

Comments please :confused:

I've been parsing the man pages but I'd like some human feedback because I'm still a dummy ;)

Specifically what's the difference between "-R" and "-r"?

I know "-R" used with "rm" removes the directory and all it's content, so does "cp -R" then copy and remove the contents of the old directory w/o the need to create a new one?

Thanks in advance. I learned long ago that if I find anything confusing someone at the forums will steer me in the right direction \\:D/

---

### Post by lithopsian on 2011-03-18
cp makes a copy and leaves the original
mv is essentially a rename, the original is gone

-r and -R do the same thing.  There are historical differences about which one can be used with certain versions of the command, but I wouldn't panic about them in Ubuntu.

---

### Post by Old *ix Geek on 2011-03-18
I'm old, too. :D And I stick with what I learned eons ago, too.

I always use -R when I do something recursively, and I believe the distinction between -r and -R has long ago been lost. So if you're used to using -R, go for it! If it's too much work pressing that [shift] key, switch to -r. ;)

---

