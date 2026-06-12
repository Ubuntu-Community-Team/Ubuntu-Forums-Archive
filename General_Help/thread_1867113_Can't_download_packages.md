---
title: "Can't download packages"
date: 2011-10-22
forum: General Help
---

### Post by futralistic on 2011-10-22
When I try to download almost anything with the software center I get an error message saying "Requires installation of untrusted packages from not authenticates sources" When I look at the details it reads "audacity audacity-data libflac++6 libportsmf0 libvamp-hostsdk3 libwxbase2.8-0 libwxgtk2.8-0".

This is obviously from audacity but I get the same message with different details from almost every package I try to download.

If I try to install audacity with the terminal I get this message ```
WARNING: The following packages cannot be authenticated!
  libflac++6 audacity-data libportsmf0 libvamp-hostsdk3 libwxbase2.8-0
  libwxgtk2.8-0 audacity
```

I am using ubuntu 11.10. This error just started, I did not have this problem until a day or so ago.

Thank you.

---

### Post by futralistic on 2011-10-23
OK. I figured it out.

I needed to check the "Source Code" box in my Update Manager, but at first it would not let me check it. Every time I tried to check the box the check would appear and then quickly disappear.

I found that I had to change my Download Server from "Server for United States" to "Main Server". After that I could check the Source Code box and resume downloading from the Software Center.

One thing I do wish someone could answer is: Why did this happen?

I never had this problem before. To my knowledge I have never had to change my Download Server, and I have certainly never encountered error messages like above.

---

