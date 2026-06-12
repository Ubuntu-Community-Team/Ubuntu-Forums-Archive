---
title: "Cannot Install GroupWise client?"
date: 2006-03-17
forum: General Help
---

### Post by Joshuwa on 2006-03-17
Has anyone sucessfully installed the Novell GroupWise client on Ubuntu?

I downloaded the client tarball from Novell's site, untarred it, and found an RPM.

Using alien, I did ```
sudo alien -i novell(rest of filename)
```

This unarchived the RPM, created a .deb, and was supposed to install it.

However, the .deb file disappeared like it is supposed to when the install is complete, but GroupWise was not installed.

I've installed GW succesfully this way in the past, so I'm not sure why it is not working with this Ubuntu installation :-k 

I appreciate any help/tips/etc.

-Josh

---

### Post by Joshuwa on 2006-03-19
Just wanted to update this, incase anyone else is installing GW on Ubuntu.

The method I used above *does* install GW perfectly. It, for some reason, does not put the icon or the destkop (as the documentation says it does), or give you any indication where it is installed.

The app gets installed in /opt, and can be opened (or linked to) from there just fine.

:)

---

### Post by sethwaynemiller on 2007-12-13
Could you explain this process in a little  more detail?  I have been trying to install the groupwise client for a few days but haven't had any luck.  I downloaded and extracted it to my desktop but haven't gotten the install to work.

If you could give as much detail as possible I'd greatly appreciate it, I'm really new to Ubuntu.

Thanks,
Seth

---

