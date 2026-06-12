---
title: "Help Setting File Target Directories"
date: 2010-09-27
forum: General Help
---

### Post by -/-benny-/- on 2010-09-27
Hey Guys

Complete noobie to the forums and to ubuntu. So I just installed the latest desktop edition of ubuntu on my laptop and all is going well. 

I have a 60gb HDD with a 10gb ext4 partition for linux, a 2gb partition for swap space and then a 
48gb NTFS partition which I wish to use as my data drive. My question is, how do I set the target directories of my document folders to be on my data drive instead of on my linux drive. 

I hope that was clear, I'll try and explain better if needed. Thanks.

---

### Post by robsoles on 2010-09-28
Welcome to UF.
 
 
 Most of me wants to tell you that you can't do that! But I'm pretty sure  someone else I once replied to went on to tell me how to do it :)
 
 You can rename (or even delete) items that 'Places->Bookmarks' point to and then replace them with symbolic links.
 
 ```
 ln -s /target_dir/dir ~/link-to-target
``` Here is a little info about the command I want you to use
 > rob@rob-desktop:~$ ln --help
 Usage: ln [OPTION]... [-T] TARGET LINK_NAME (1st form)
 ...
...

  -s, --symbolic make symbolic links instead of hard links
 
... So, if your 48Gb NTFS partition is mounted at /media/data (by entry in  /etc/fstab) and you called your documents folder in that file-space  'docs' then this would be the sequence of commands for terminal:```
mv  ~/Documents ~/not-my-docs
ln -s /media/data/docs ~/Documents
```Then test it by clicking it out of places.

I haven't tried it so do protest if it doesn't work, for sure!

I would hesitate and research it for a long time before doing it to a  ~/Desktop I rely on but ~/Downloads is probably OK to shift this way and  ~/Music and ~/Pictures and ~/Videos should be fine too.

---

