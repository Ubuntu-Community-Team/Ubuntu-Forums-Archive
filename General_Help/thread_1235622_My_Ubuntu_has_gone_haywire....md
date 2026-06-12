---
title: "My Ubuntu has gone haywire..."
date: 2009-08-09
forum: General Help
---

### Post by FoxTheCave on 2009-08-09
Please help all, my Ubuntu has suddenly gone haywire!

For no discernible reason, it's just started acting extremely strange. Here's a lowdown of things i've noticed so far:

Cookies aren't being accessed by Firefox, meaning that sites where i'm normally logged in as soon as I arrive, i'm suddenly not. Not a big deal, but still odd.
[LIST]
[*]The "search google" thing on the top right hand corner of my Firefox browser doesn't work.

[*]The "back" and "forwards" buttons in Firefox no longer work.

[*]There's a random grey space below the address bar and above the "tab bar (if thats what its called), like another empty bar that wasn't ever there before in Firefox.

[*]Again in Firefox, my Bookmarks don't load, and it takes about a minute for the menu to come up, as if Ubuntu is trying to find the data but for some reason it can't.

[*]MSN won't load.

[*]Firefox randomly closes.

[*]The locations I had added to the sidebar that labelled "Places" in the file browser have suddenly all disappeared, and when I try to drag the folders back onto the sidebar, then appear for a second and then disappear.

[*]Before, a video file would load a preview image in the file browser - now it does not show a preview image, instead just shows the white logo it normally made when it was loading the preview image.

[*]The text on certain webpages is suddenly very big.

[*]Youtube videos stop after fifteen seconds, even though they continue loading, the video just stops.
[/LIST]

This all suddenly happened overnight, i'ms sure there's more stuff too, but this is all i've noticed. I was thinking it was a virus, but isn't Linux supposed to be secure from viruses? I'm seriously thinking about uninstalling and reinstalling, but if anyone has a simpler solution...? Or even just any idea's...?

It's Ubuntu 8.04 Hardy Heron btw.

Please help me!

---

### Post by Barafu Albino Cheetah on 2009-08-09
First things to check: 
1) you have enough free space for ubuntu. do df -H /dev/sda1 or whatever partitions you have. 
2) you have write acces to your home directory. do chown -R username /home/username and chmod -R u+rwx /home/username/

then try creting a new user, and log in as it. 
then try purging and reinstalling firefox to see if it fixes. purge xulrunner too.

---

### Post by FoxTheCave on 2009-08-09
I'm such a ******* moron! Thanks so much, it was so simple - I had run out of free space, and I guess that affected how the system worked. My God,i'm so ******* stupid!

Edit: Wait hold on, youtube vids still aren't working...let me restart and see if that fixes that...

Second Edit: Yep, fixed it.

---

