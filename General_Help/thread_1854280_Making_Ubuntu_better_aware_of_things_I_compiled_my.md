---
title: "Making Ubuntu better aware of things I compiled myself?"
date: 2011-10-04
forum: General Help
---

### Post by KonfuseKitty on 2011-10-04
After I compiled something from source myself, I often find that Ubuntu isn't aware of it, making it more difficult to keep track of versions. Is there a way of 'registering' the compiled software with the system? Any bash commands that would help?

---

### Post by dcstar on 2011-10-04
> **KonfuseKitty said:**
> After I compiled something from source myself, I often find that Ubuntu isn't aware of it, making it more difficult to keep track of versions. Is there a way of 'registering' the compiled software with the system? Any bash commands that would help?

Make a .deb package and install that.

---

### Post by mcduck on 2011-10-04
> **KonfuseKitty said:**
> After I compiled something from source myself, I often find that Ubuntu isn't aware of it, making it more difficult to keep track of versions. Is there a way of 'registering' the compiled software with the system? Any bash commands that would help?

Yes. You can use checkinstall to turn the compiled program into a .deb package and then install it though Ubuntu's package management. This allows you to maintain your compiled programs just like any other package.

All you need to do is install checkinstall from the repositories, and then when compiling programs, instead of running "sudo make install" you run "sudo checkinstall".

(Checkinstall doesn't create proper .deb packages suitable for distributing your programs, though, as it doesn't add all the required additional information about dependencies etc. so they are only really good for use on the machine where you compiled the code)

---

### Post by KonfuseKitty on 2011-10-04
Thank you, that's very useful info. Going further than what checkinstall can do, is there a way of creating the full package, with dependencies?

---

### Post by mcduck on 2011-10-04
AS far as I know there's no simple or automatic way to do that, but this seems to be quite a good guide to packaging things properly: [http://www.webupd8.org/2010/01/how-to-create-deb-package-ubuntu-debian.html]("http://www.webupd8.org/2010/01/how-to-create-deb-package-ubuntu-debian.html")

---

