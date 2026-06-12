---
title: "Is it possible to have &gt; 1 /home partition"
date: 2011-06-15
forum: General Help
---

### Post by Phil Stone on 2011-06-15
If I were to set up several distro's on a single hard disk, and I wanted to - for the sake of argument - give each distro their own /home partition would this cause any technical problems? 

I understand that this could easily lead to human error but I want to know if it is actually possible (assuming all set up correctly) or would this cause actual sytem malfunctions during booting for example.

---

### Post by Elfy on 2011-06-15
Should be fine as each will know which is it's /home.

In fact it's probably better to do it that way. If you have the same home it can issues with different OS's using different UID's - ubuntu for instance starts at 1000 fedora at 500. They might well have different versions of apps you use.

---

### Post by seawolf167 on 2011-06-15
> **forestpiskie said:**
> In fact it's probably better to do it that way. If you have the same home it can issues with different OS's using different UID's - ubuntu for instance starts at 1000 fedora at 500. They might well have different versions of apps you use.

Came here to say this - (IMO) you actually don't want to use the same /home partition for multiple distros. I've only ever had problems with different versions of programs on different distros changing their config files, etc.

---

### Post by Phil Stone on 2011-06-15
ah great. thanks.

---

### Post by nothingspecial on 2011-06-15
On the other hand, the same /home for different supported *buntu flavours ,at the same version, is fine.

**Edit** By that I mean, if you wanted xubuntu 11.04 and edubnuntu 11.04, you could use the same home partition, as long as you add your users in the same order.

---

### Post by srs5694 on 2011-06-15
IMO, it's better to use a single /home partition across distributions. You should *not*, however, use the same *home directory* across distributions. The distinction is linguistically subtle but extremely important:


[list]
[*]The /home directory (or partition) is where Linux creates subdirectories for each user's files.
[*]Each user has *a home directory* that is a subdirectory of /home in which that user stores files. For instance, mine is /home/rodsmith on most of my computers (I have several).
[/list]


If you use a single /home partition for all your distributions, you can create separate user home directories for each one. For instance, on some of my multi-boot systems, I use home directories like /home/rodsmith-f15 (for Fedora15) or /home/rodsmith-s (for SUSE). This is most easily done by using different usernames on each distribution; however, there are ways to do it by using usermod or options in more advanced account-creation tools that create user home directory names that aren't identical to the username.

Using a single /home directory enables you to consolidate your disk space, rather than carving it up into tiny bits. This makes it much easier to manage that space, should you get anywhere close to filling it up.

---

