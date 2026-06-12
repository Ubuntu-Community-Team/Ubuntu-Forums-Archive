---
title: "Thunar, Gigolo and browsing network shares in xfce"
date: 2012-06-05
forum: General Help
---

### Post by oregonbob on 2012-06-05
I am new to xfce (xubuntu 11.10) and was surprised at the featureless, unfriendly Thunar is used instead of Nautilus. Apparently Thunar cannot browse network shares (and many other things) the way Nautilus can. I have read and tried numerous work-arounds but none work very well. So I was wondering if anyone else has a solid recipe for network shares in Thunar?

The common Thunar error message when trying to browse a windows network: "Failed to open workgroup, Failed to retrieve share list from server"

I tried Gigolo, which seems like a lot of hassle just to access shares, as though it should have been a built-in capability in Thunar. In addition when I use Gigolo to add a share and then open the share it appears to change my whole desktop when it opens.

Any good recipes for browsing networks like we are all used to doing?

I saw a note that merely installing Nautilus on xubuntu will "screw up the system". Is that still true?

---

### Post by eyeofliberty on 2012-06-05
I don't use Xfce and Thunar myself, but it is my understanding that Xfce 4.10/Thunar 1.3 (?) is able to browse network drives. Can anyone confirm this?

Having said that, I don't see any reason why you can't install Nautilus from the repositories, and use that as your file manager. I know others do this.

---

### Post by Morbius1 on 2012-06-05
* Thunar can browse the network just like nautilus - in fact it's using the same backend. What Thunar cannot do is create a bookmark ( misnamed becasue it's really a "nautilus launcher" ) to a remote share the way Nautilus can. 

* If you are using Gigolo - which is a gem of an application btw - and "it appears to change my whole desktop when it opens" you have some kind of issue with your install.

*>  I saw a note that merely installing Nautilus on xubuntu will "screw up the system". Is that still true?     Some people will swear that it does not. Installing it for me has - and that includes a VBox Xubuntu 12.04 guest that I use for this kind of thing -  always ended badly.

---

### Post by oregonbob on 2012-06-05
> **Morbius1 said:**
> Gigolo - which is a gem of an application btw

Gem? What is gem about needing a whole additional application to browse network shares when that functionality is built-in to most other file managers? I don't get it.

---

### Post by Toz on 2012-06-06
Have you installed gvfs-backends? Thunar depends on it to be able to browse network shares.

---

### Post by Morbius1 on 2012-06-06
> **oregonbob said:**
> Gem? What is gem about needing a whole additional application to browse network shares when that functionality is built-in to most other file managers? I don't get it.
** Thunar can browse the network - it's built in - just like any other file manager.

If it can't for you and given the comment about Gigolo messing up your desktop would indicate to me something is wrong with your install.

** Toz brings up a good point - maybe you are missing some packages. In addition to gvfs-backends you might also want to check for gvfs-fuse.

** Gigilo is a gem because of one added feature. It allows the user to automount remote shares at login. It does that without requiring you to fiddle around with fstab and it can even wait for the remote machine to be up and operational before it attempts to mount it's share. It also saves the credentials ( if there are any ) in the keyring for added security. Outstanding!

---

### Post by scottbomb on 2012-06-06
TOZ is correct. gvfs-backends fixed it for me. It should be installed by default, but it's not. I have never needed to use gigolo. I also use a Samba GUI (the exact name of which I cannot remember) that allows me to designate my shared folders so that other machines can browse them.

---

### Post by LewisTM on 2012-06-06
Gigolo is XFCE's answer to the remote bookmarks found in Nautilus.
At first I was like you: "What? I can't save connections to FTP/SFTP/Samba locations?"

But Gigolo offers those bookmarks and having them in a separate, centralized control center started to make sense. The Places menu, the Desktop and Thunar are much less cluttered without network shortcuts everywhere. I still miss being able to intuitively browse the locations in a tree view.

Cheers!

---

### Post by node8472 on 2012-06-19
In _**my own**_ recent experience with xubuntu (which I've just switched to) just installing nautilus won't cause apocalyptic computer meltdown. :cry::lolflag:

However using "nautilus --desktop" did cause some negative side affects, wallpaper was an ugly blue which I couldn't change (missing dependences so to speak) this also brings back the familiar ubuntu desktop context menu.  Virtual machines are great for testing out ideas :D

On the subject of thunar not browsing network shares, I'd like to point out there is a network shortcut by default in xubuntu's thunar. (if you only installed xfce not xubuntu-desktop you might be missing the xubuntu configs for thunar and the gvfs back-ends) I'm looking for a thunar-shares-plugin/nautilus-share type solution for creation of samba shares

---

### Post by Toz on 2012-06-19
> **node8472 said:**
> I'm looking for a thunar-shares-plugin/nautilus-share type solution for creation of samba shares

You could try a thunar custom action. See: [http://ubuntuforums.org/showpost.php?p=11505823&postcount=7]("http://ubuntuforums.org/showpost.php?p=11505823&postcount=7")

---

### Post by Bucky Ball on 2012-06-20
Or you could install Nautilus! Runs fine in Xfce (I use PCmanFM from LXDE myself). Xfce also has no 'Connect to Server' option which I liked. 

Personally, I do all file transfers between machines with Filezilla (and yes, I use xfce). ;)

PS: I have used Nautilus in XFCE on several machines with absolutely no problems ever, period. Agreed, others have.

---

### Post by mosaic2s on 2012-06-25
I am trying out xubuntu 12.04 to avoid unity - HUD is good but time delay is cumbersome.

Only thing I am missing in THUNAR is F3 function that gives me another window in nautilus.

---

### Post by lightning slinger on 2012-06-25
> **mosaic2s said:**
> 

Only thing I am missing in THUNAR is F3 function that gives me another window in nautilus.

<Super>+f
will open you another window in thunar by default!
Look under Settings>Keyboard>Application Shortcuts  for others!
In fact you could even assign F3 to open another window in thunar in place of <super>f

---

### Post by mosaic2s on 2012-06-25
<super>+f only opens another instance of thunar.
F3 in nautilus opens another pane within the same window.

Thanks for showing the keyboard settings. I now use <super>+w for web browser and <super>+t for terminal.

---

### Post by Bucky Ball on 2012-06-25
I thought it was control+t, like Firefox, if you are talking about opening a new tab in a single instance of Thunar.

---

### Post by mosaic2s on 2012-06-25
nope.

---

### Post by Bucky Ball on 2012-06-25
Ok. Working for me that way in PCmanFM (which is faster than all of 'em).

(* Just tried in Thunar and control+t takes away the left pane.)

---

