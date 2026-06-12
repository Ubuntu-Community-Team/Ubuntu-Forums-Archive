---
title: "Share /home partition"
date: 2010-09-27
forum: General Help
---

### Post by 0N3 on 2010-09-27
Is it possible to share this partition between Ubuntu & Kubuntu?

---

### Post by searchfgold6789 on 2010-09-27
have you tried
```
ln -s name-of-source-file name-of-new-directory
```

---

### Post by 0N3 on 2010-09-27
Im gonna install it onto a portable USB drive its basically for testing purposes and giving it a spin i much prefer gnome desktop but im just curious as to how the look and feel of Kubuntu is thanks for the quick reply.

---

### Post by 0N3 on 2010-09-27
Will your post about getting all the commands and symbols make it easy for me to make the Euro symbol?

---

### Post by nothingspecial on 2010-09-27
> **0N3 said:**
> Is it possible to share this partition between Ubuntu & Kubuntu?

Yes it is possible

---

### Post by srs5694 on 2010-09-27
> **0N3 said:**
> Is it possible to share this partition between Ubuntu & Kubuntu?

Yes. As a general rule, though, it's best to set up separate home *directories* for each user. These can all reside in /home, though. The easiest way to do this is to use different usernames for each installation, as in fredu (on Ubuntu, say) for one installation and fredk (on Kubuntu, say) for another. This will create /home/fredu and /home/fredk home directories, which won't interfere with one another. Alternatively, there are advanced account-creation options that enable you to specify a home directory that's different from the username, so you could have the same username on both systems but use different home directories.

That said, I'm not sure that this is as necessary for two closely-related distributions like Ubuntu and Kubuntu. The reason it's helpful in general is that different distributions often have slightly different versions of user programs, and these programs often change their configuration file formats over time, so when the older program in one distribution reads the configuration file for the newer version of the same program that ships with another distribution, wackiness can happen. Also, icons and programs locations can vary between distributions, which can make desktop environments and icons in other programs look bad or even be missing altogether. Since Ubuntu and Kubuntu are so closely related, these reasons might not be as important; however, it's better to be safe than sorry, so I'd create separate home directories nonetheless.

---

### Post by nothingspecial on 2010-09-27
I`ve shared /home between various buntus

Never a problem, even with #! 

Not a good idea between completly different distros though

---

