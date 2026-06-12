---
title: "Thunar stuck &quot;loading folder contents...&quot;"
date: 2010-02-19
forum: General Help
---

### Post by eriffo on 2010-02-19
I'm running Xubuntu Karmic.
When I open some folders with Thunar, even if they don't have more than a few files in them, it takes a very long time to show the contents. Sometimes up to two minutes. It happens almost always if the folder is on my ntfs partition, but sometimes even when it's at /home.
I used to run Ubuntu Hardy, and nothing like this ever happened with Nautilus.
Any ideas what might be wrong?

---

### Post by eriffo on 2010-04-14
bump

---

### Post by akakingess on 2010-04-14
The only thing that I could suggest is to start the ol' trial and error method. First off, try installing Nautilus or PCManFM and run those and see if you get the same results, then we will know if it is system related or solely Thunar causing the problems. From there, we can start trashing or redoing Thunar configs if the other file managers work just fine. Unless you want to just choose to switch to a different file manager. Let us know how it goes and we can try to take it just a couple steps at a time.

ALSO: Have you checked Launchpad.net to see if this problem has already been reported by others with issues with Thunar?

---

### Post by eriffo on 2010-04-14
Thanks for your reply!

I installed Nautilus and made it race Thunar. I tried to open some random folder in the ntfs partition with thunar (actually a subfolder, which is when the problem happens). Then opened nautilus and tried to open the same folder. It was kinda slow, but just the usual for nautilus, and it still beat thunar by at least a couple of minutes.
Then I did the same thing but one file manager at a time. Thunar took forever, Nautilus no time.

I found [this]("https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/445236") in Launchpad, but wasn't much help. What it describes is somewhat similar, but not quite. I have the problem with a ntfs partition, not a fat one (which I also have). No usefree option in my fstab, but I doubt that's where the problem is, since nautilus works fine.

---

### Post by akakingess on 2010-04-14
Just a quick question, but do you have ntfs3g installed (available within Synaptic Package Manager)?

---

### Post by eriffo on 2010-04-14
yes.

---

### Post by akakingess on 2010-04-14
So, it appears that the problem is with Thunar and not necessarily system-wide, am I understanding correctly? If so, than now we need to start troubleshooting Thunar, of course uninstalling (purging) and reinstalling would be a good place to start.

---

### Post by eriffo on 2010-04-14
yes, the problem is limited to thunar. I tried reinstalling it a while back, but without uninstalling it first (just marked for re-installation in Synaptic). Does it make a difference? Also, how do I purge it? Mark for complete removal?

---

### Post by akakingess on 2010-04-14
Yes, you can mark for complete removal, but via the command line I think it goes something like this "sudo aptitude purge thunar"  or it may be thunar purge, but either way it will clean out everything so that you can start from scratch with a fresh install.

---

### Post by eriffo on 2010-04-14
[FONT="Courier New"]sudo apt-get purge thunar[/FONT] does this:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libsoup2.2-8
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  thunar* thunar-archive-plugin* thunar-media-tags-plugin*
  thunar-thumbnailers* thunar-volman* xfce4-places-plugin* xubuntu-desktop*
0 upgraded, 0 newly installed, 7 to remove and 191 not upgraded.
After this operation, 2,986kB disk space will be freed.
Do you want to continue [Y/n]?
```

I'm concerned about removing that last package, xubuntu-desktop. Won't that cause a mess?

---

### Post by akakingess on 2010-04-14
Not quite sure about that as I use Gnome, but the worst case scenario would be that you need to reinstall it (xubuntu-desktop that is) which I know may be a pain, but if you really want to use Thunar, you may need to jump through some hoops to get it running back to normal. Sorry about not knowing more about XFCE, i should learn all of the desktops, but I am too busy looking for a job and learning C++, scripting, CGI, etc. to experiment with the computer too much. My apologies, but I guess that's going to have to be your call.

---

### Post by ck_linux on 2010-05-07
[eriffo]("http://ubuntuforums.org/member.php?u=676180"),
maybe the same problem. I just opened a new thread with title "[B]xubuntu 10.4 + thunar"
**and contents:**
[/B] 			
 			 			 		   		 		 		Most of the  time, thunar freezes. You can however go to a directory, select a file,  but can not open.
And I know: permissions are ok, the system knows with what application  to open.

Is your problem solved ?

---

### Post by eriffo on 2010-05-07
Haven't solved it yet.
My problem is similar, but not identical I think. In my case thunar doesn't freeze, it just takes a long time to open a folder. You could say it freezes for a while, but then it works fine. It gets stuck "loading contents", but doesn't show any files during that time. Once it's done "loading" I can open files no problem.
What you mentioned in your thread that's very similar is that the problems occur when I try to go deeper than 1 level into a folder.
What filesystem are you having trouble with? In my case it's ntfs, and ext3 (although very rarely). I don't recall having any trouble with my fat32 partition, though.

I'll keep an eye on your thread.

---

