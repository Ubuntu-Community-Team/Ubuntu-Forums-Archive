---
title: "Why don't my downloaded files appear where they are supposed to have been saved?"
date: 2012-06-01
forum: General Help
---

### Post by Manmadegod on 2012-06-01
You set Firefox to save downloaded files in your /home/username/Downloads folder, but Thunar does not show it in that folder when you navigate to that folder to look for it. This puts you in a situation that your only means of viewing that pdf is through the Firefox Downloads window, which DOES show your downloaded file, but will not help you save it!  So you go back into your Firefox Preferences and check it again, and this time click on the Browse button on the "Save Files to" line with Downloads appearing in the box. There they are, all those files which you saved in the same folder last night (saved by other programs, but the one which you just downloaded today through Firefox is still missing), so you know you are asking it to save to your user Download folder, not something created by Firefox under its own path.

As if that weren't enough of a WTF, here's what happened when I decided I would find that file even if I had to search my whole computer for it. I right-clicked my user folder in Thunar to bring up Catfish, and punched in the first several characters of my file. There were no filter buttons engaged to limit my search in any way, least of all an exact match, but then Catfish didn't even look at my system. Instead, I got an instantaneous "Fatal Error, Search Was Aborted" error.  Sorry if I repeat myself, but  WTFWTFWTF!!!!!

It's made even more insteresting in that the file which I had downloaded, and was desperately trying to save happened to be "Getting Started with Ubuntu 11.10.pdf". Although I use Xubuntu, and would like some specific help on using the Xubuntu shell (how can anyone associate himself with the Unity shell by documenting it and not be mortally embarrassed),  it was this document which is available for what use I can make of it.  Is the most powerful Linux distro ever to target PC users too poor now to host its product documentation online? 

Does it need mentioning the sheer irony of all this, just to save a .pdf file? At this point, if I were to sing the praises on the functional ingenuity of Linux development, an example such as this would have me drowned out several times over with hysterical laughter.  When it comes to pushing it's users into utter insanity, they are known for their ingenuity at that!

Well, in a nutshell, I need to know why Firefox won't really save my download, and what makes Catfish crap the bed with those search-abort errors.

Thanks.

---

### Post by LewisTM on 2012-06-01
Strangely Firefox stores all downloads in /tmp regardless of what dir you pick.
Also you can't open the containing folder from the Downloads box. 
Those look like Xubuntu-specific bugs. 
I hadn't seen them before since I use Chrome, which works fine in all regards.

As for Catfish, it seems to be picky about the search syntax when using the 'locate' method; you can't add spaces and special characters like $ or ! or whatnot. The 'find' method is more robust but slower.

Cheers!

---

