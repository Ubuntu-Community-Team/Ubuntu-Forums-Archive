---
title: "Apt-cacher help!"
date: 2009-10-07
forum: General Help
---

### Post by odin06 on 2009-10-07
Hi to All!

Im a super noob in ubuntu and im just starting to discover its strengths, one of them is APT-CACHE/APT-CACHER. Imagine a local repository that saves a lot of your bandwidth. Now back to my concern, ive done a "Server-Client" of APT-CACHER already, but im getting this message when i enter the sudo apt-get update to my ubuntu client,

"Failed to fetch [http://192.168.2.44/ubuntu/dists/jaunty-updates/universe/source/Sources](http://192.168.2.44/ubuntu/dists/jaunty-updates/universe/source/Sources) 403 Sorry, not allowed to fetch that type of file: Packages"

Am i missing something? coz im pretty sure i followed the Ubuntu Tech Docs correctly. 

Need your help on this guys.. Thank you very much!

---

### Post by arnold.pietersen on 2009-10-19
Hi Odin06

I have also struggled a bit setting up apt-cacher being new to the technical side of Ubuntu Linux. However, I have succeeded. 

There is something missing in your address.  After the 44 you should have 3142. Thus your address should read something like

[http://192.168.2.44:3142/ubuntu/dists/jau...source/Sources](http://192.168.2.44:3142/ubuntu/dists/jau...source/Sources)

I hope this helps.

---

