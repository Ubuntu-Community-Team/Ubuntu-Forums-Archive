---
title: "Red triangle for no reason"
date: 2011-07-12
forum: General Help
---

### Post by paradoja on 2011-07-12
Hello, I've installed Ubuntu five months ago, and updated to 11.04. About two months ago, a red triangle started appearing in tray from now and then, with this message:

> The update information is outdated. This may be caused by network problems or by a repository that is no longer available. Please update manually by clicking on this icon and then selecting 'Check for updates' and check if some of the listed repositories fail.

When I open the Update Manager to check for updates, it says:

> Failed to download repository information

Check your Internet connection.

Details: 

W:Failed to fetch [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/natty/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/natty/main/binary-i386/Packages](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/natty/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

My connection is just fine, and when there actually are updates, everything works great, so I don't understand why the red triangle goes on showing up in tray.

I googled this issue several times to find solutions, but nothing worked. I'm mostly curious, because this doesn't seem to be trouble regarding updates. I hope anybody knows what's this about!!

Thanks!!

---

### Post by JedMeister on 2011-07-13
And the reason is that there are no Natty packages in the XBMC PPA. To remove the error, remove the PPA from your sources. Or you could try setting it to Maverick (10.10) rather than Natty. But be warned that could have unintended results (could be problems with packages and unmet dependencies etc).

---

### Post by paradoja on 2011-07-13
Ok, that was simple! I prefer not to remove anything. The red triangle is just a minor detail. I just wondered.
I'm not an Ubuntu expert, so may be this question is a little bit naive, but anyway: will there be packages in the XBMC PPA? Or may be in 11.10? I don't know what they are though, I suppose it's about the packages which are necessary for updates.

---

### Post by wildmanne39 on 2011-07-13
> **paradoja said:**
> Ok, that was simple! I prefer not to remove anything. The red triangle is just a minor detail. I just wondered.
I'm not an Ubuntu expert, so may be this question is a little bit naive, but anyway: will there be packages in the XBMC PPA? Or may be in 11.10? I don't know what they are though, I suppose it's about the packages which are necessary for updates.Hi, no it will not be, I did not find it listed in synaptic and it is a luanchpad ppa, and you can just uncheck the ppa you do not have to remove it.

---

### Post by JedMeister on 2011-07-13
To find out if there are plans to update the XBMC PPA with Natty packages is to ask them (that is the XBMC team). They are unofficial Ubuntu packages (although in this particular case they are the official packages for XBMC if you follow me). If you don't have XBMC (XBox Media Centre) installed (or any of the packages that PPA provides it won't do any harm to remove (or as wildmanne39 suggests just untick it). An easy way to see if you have any packages installed from the XBMC PPA is to open Synaptic and select 'Source' in the bottom left corner. Then find the PPA in the repos listed (top left), then you can browse through the packages and if none are installed then you may as well delete it. If any are installed, you may be able to find an alternative place to get them from.

---

### Post by paradoja on 2011-07-13
Thank you all very much. 
I don't have XBMC installed. I went to Synaptic to do what you said, but I don't have a "Source" option in the bottom left corner. (Sorry that you have to chat with a newbie.)

After all the little trouble that brought me updating to 11.04 (I hated Unity, but I managed to turn it back to the classic Ubuntu) -like some apps not working-, I don't know if I'll ever update again, unless 11.10 is a dream-ubuntu...

---

### Post by wildmanne39 on 2011-07-13
> **paradoja said:**
> Thank you all very much. 
I don't have XBMC installed. I went to Synaptic to do what you said, but I don't have a "Source" option in the bottom left corner. (Sorry that you have to chat with a newbie.)

After all the little trouble that brought me updating to 11.04 (I hated Unity, but I managed to turn it back to the classic Ubuntu) -like some apps not working-, I don't know if I'll ever update again, unless 11.10 is a dream-ubuntu...Hi, I understand some people have had trouble with unity while others have not, enjoy 10.10.

---

### Post by JedMeister on 2011-07-13
> **paradoja said:**
> Thank you all very much. 
I don't have XBMC installed. I went to Synaptic to do what you said, but I don't have a "Source" option in the bottom left corner. (Sorry that you have to chat with a newbie.)

After all the little trouble that brought me updating to 11.04 (I hated Unity, but I managed to turn it back to the classic Ubuntu) -like some apps not working-, I don't know if I'll ever update again, unless 11.10 is a dream-ubuntu...

Ooops. Just double checked and its 'Origin' not 'Source' Sorry about that. Personally I don't go much on Unity either so I chose to stick with Lucid and Gnome 2. I have made so many modifications though that its not quite Lucid anymore! Not sure what I'll do when support ends? Perhaps I'll go to Mint? I guess I'll just wait and see. I did toy with the idea of going to Debian but I missed the PPAs too much.

Anyway back on topic: Another thing you could do to see if you have any packages installed from that PPA is to open Synaptic again. Select 'Status' in the bottom left cnr (I checked this time!) and look for "installed (local or obsolete". I'm pretty sure that any packages from repos that you can't contact should show up there. If you don't have anything there try opening software sources and untick the PPA, Refresh packages and check again (shouldn't make any difference). If you have packages there I think right-click on the package > Properties > Version tab should give the repo in brackets. Otherwise apt-cache show packagename should give you all the details of the poackages.

Bottomline though is that just unchecking the PPA will stop the errors and won't do any damage, just the any packages installed from that repo won't be updated.

---

### Post by paradoja on 2011-07-18
Thanks a lot. I checked what you told me, though I decided not to touch anything for the moment... I'm not quite an expert or anything, and I'm afraid to make a mess.

---

