---
title: "Creating symbolic links for ntfs partitions in ubuntu"
date: 2011-10-24
forum: General Help
---

### Post by eltommo on 2011-10-24
Hello,

I am looking for a command line tool that will allow me to create symbolic links within ntfs partitions from ubuntu (or any other linux distro really).
Does such a tool exist?

Thanks

---

### Post by mikejonesey on 2011-10-24
add windows disk to fstab to auto mount then add a sym link with usual syntax ln -s /from /to

:)

---

### Post by eltommo on 2011-10-24
Oh, I didn't think links created under ln would be recognized under linux. Thanks, testing now...

---

### Post by eltommo on 2011-10-24
Nope, no success :(
The link is understood in ubuntu, but no under windows.

---

### Post by Lars Noodén on 2011-10-24
> **eltommo said:**
> Nope, no success :(
The link is understood in ubuntu, but no under windows.

It was my understanding that, if you read the fine print, [NTFS cannot do symlinks](http://en.wikipedia.org/wiki/Comparison_of_file_systems#Features).  It's unfortunate that it is hard/impossible to use better filesystems under Windows.

---

### Post by eltommo on 2011-10-24
> **Lars Noodén said:**
> It was my understanding that, if you read the fine print, [NTFS cannot do symlinks]("http://en.wikipedia.org/wiki/Comparison_of_file_systems#Features").  It's unfortunate that it is hard/impossible to use better filesystems under Windows.

I believe it is possible in versions of NTFS above 5.0. It's possible to use the mklink command under windows to achieve symbolic links, but I would prefer to do directory and file rearranging under ubuntu because the windows command system is, well, terrible.

---

### Post by dcstar on 2011-10-25
> **eltommo said:**
> I believe it is possible in versions of NTFS above 5.0. It's possible to use the mklink command under windows to achieve symbolic links, but I would prefer to do directory and file rearranging under ubuntu because the windows command system is, well, terrible.

Since NTFS is incompatible with Linux filesystems in so many ways, I would be surprised if you could make links to it and shocked if they actually functioned correctly without eventually corrupting something.

---

### Post by Mark Phelps on 2011-10-25
I was surprised to read that NTFS can't do symbolic links because with Vista, MS introduced their concept of "junctions" -- nothing more than symbolic links.

See note below:
> As of Windows Vista, NTFS fully supports soft links. See this Microsoft article on Vista kernel improvements. NTFS 5.0 (Windows 2000) and higher can create junctions, which allow any valid local directory (but not individual files) ("target" of junction) to be mapped to an NTFS version thereof ("source" = location of junction). The source directory must lie on an NTFS 5+ partition, but the target directory can lie on any valid local partition and needn't be NTFS. Junctions are implemented through reparse points, which allow the normal process of filename resolution to be extended in a flexible manner.

Actually, if I understand your problem, you want to create links in NTFS -to- nodes in the Linux filesystem -- and THAT is the problem.  MS Windows can't read Linux filesystems, at least, not without third party drivers and those have limitations that might prevent sim links from working.

---

### Post by th00ht on 2012-02-25
> **Lars Noodén said:**
> It was my understanding that, if you read the fine print, [NTFS cannot do symlinks](http://en.wikipedia.org/wiki/Comparison_of_file_systems#Features).  It's unfortunate that it is hard/impossible to use better filesystems under Windows.

You're wrong. Of course NTFS can do symlinks or reparse points.:o

---

### Post by th00ht on 2012-02-25
> **dcstar said:**
> Since NTFS is incompatible with Linux filesystems in so many ways, I would be surprised if you could make links to it and shocked if they actually functioned correctly without eventually corrupting something.

What do you mean with incompatible? it is possible to mount ntfs formatted partitions. The only think needed is that the ntfs developers at debian make a transparent ln for ntfs partitions. Easy peasy.:)

---

### Post by Mark Phelps on 2012-02-25
> **th00ht said:**
> You're wrong. Of course NTFS can do symlinks or reparse points.:o

Which I already mentioned MONTHS ago ... and your point in repeating what I already mentioned is ???

---

