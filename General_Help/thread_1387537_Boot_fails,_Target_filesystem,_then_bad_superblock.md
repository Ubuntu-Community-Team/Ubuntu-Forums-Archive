---
title: "Boot fails, Target filesystem, then bad superblock"
date: 2010-01-22
forum: General Help
---

### Post by WASHAD on 2010-01-22
Hello fellow Ubuntu users, thanks for taking the time to read this post. 

In the last two months this is the third time that I have had problems with boot up. I usually find a post on how to fix it, but I'm stuck this time. 


On bootup:

mount /dev/dis ................. on /root -> failed invalid argument
{some other failures}
target filesystem doesn't have /sbin/init. 


Most of the posts call for using live CD, and mounting it. 

```
sudo mkdir /media/root
sudo mount /dev/sda2 /media/root
```
(yes, my linux is on sda2)

When I try to mount, I get;

> 
wrong fs type, bad option, bad superblock on /dev/sda2, missing codepage or helper program or other error. In some cases useful info is found in syslog - try dmesg | tail or so

dmesg gives me a whole lot of stuff. Somewhere near the end, though, I get a couple messages. 

> EXT3 - fs error (device sda2): ext3_check_descriptors: block bitmap for group 6 not in group (block 174.....)!

> EXT3 - fs: group descriptors corrupted


Please be gentle with your responses. Though I'm not brand-new to Ubuntu, I'm still fairly new and need some hand-holding,

thanks.

---

### Post by WASHAD on 2010-01-22
OK, well after an hour or so of searching, I found the command to fix my problem; I'll post it here for others;

1. Boot live CD
2. Run Terminal
3. type "sudo fsck -f/dev/sda2"  (your drive may be different than sda2)
4. I had to respond 'y' to the fix (y/n)? prompt literally about a thousand times. 
5. Problem fixed. 



Any ideas as to why this happens to me regularly? I don't buy the bad hard-drive argument. My search shows that this is common to people after certain upgrades and installs. Also, my Windows boots fine everytime - even when my Linux corrupts. I don't think that my hard drive is playing favorites :)

SteveJ

---

