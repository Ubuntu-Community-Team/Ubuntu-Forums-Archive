---
title: "Link to NTFS drive"
date: 2012-05-15
forum: General Help
---

### Post by poumtatalia on 2012-05-15
Hello, 

I just installed Ubuntu 12.04 and i'm trying to create a link to an NTFS drive but the "Make Link" menu is not available for any of the folders of my NTFS drives.
Any way around this?

Thanks for your help.

---

### Post by coffeecat on 2012-05-15
See my screenshot for the right-click context menu for a folder in a mounted NTFS partition. Are you not seeing the "make link" choice about halfway down?

If you are not, are you mounting the NTFS partition from the nautilus file browser or have you added a line to /etc/fstab? If the latter, post the contents of your /etc/fstab file.

You can create symlinks by using the terminal but the GUI way is convenient. I've never seen the make link option disappear from the context menu, but let's confirm that is indeed what has happened for you.

---

### Post by prshah on 2012-05-15
> **poumtatalia said:**
> I just installed Ubuntu 12.04 and i'm trying to create a link to an NTFS drive but the "Make Link" menu is not available for any of the folders of my NTFS drives.
Any way around this?

By "not available" do you mean it is "greyed out"? This can happen if the device you are browsing on does not have write permissions.

By default, NTFS devices are mounted with write permissions for users in the "fuse"/"plugdev" group, so this should not be your problem unless you have manually mounted it using "sudo" or so.

Another possibility is that you are trying the link to the "root" (so to speak) of the NTFS device; eg are you trying to create this link in "/media"? This will fail, because you cannot create links in "/media" as an unprivilidged user. You can choose to browse this directory as superuser, or better yet, use the terminal to create the link.

Please post back if you need more information.

---

