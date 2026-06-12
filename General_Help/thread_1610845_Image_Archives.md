---
title: "Image Archives"
date: 2010-11-01
forum: General Help
---

### Post by Legeril on 2010-11-01
I have a archive placed in an image .jpeg, in windows I can just open the .jpg with Winrar or similar how would I got about opening the archive in Linux? Do I need to download a similar app or can it be done say through the a native app or command line?

---

### Post by jesuisbenjamin on 2010-11-01
It depends on the extension of the file. Mostly the Archive Manager will do the job. For RAR and ZIP7 or other obscure compression you may need to add patches or use different programs. I don't have the info at hand right now but you can type the extension you seek to de-compress in your Ubuntu Software Center.

B.

---

### Post by Legeril on 2010-11-01
The files are inside an image, the extension is .jpg.

---

### Post by HermanAB on 2010-11-01
Rar is not Free, so there is no default support for it on Linux.

---

### Post by Legeril on 2010-11-01
> **HermanAB said:**
> Rar is not Free, so there is no default support for it on Linux.

Yea I am aware of that, it sucks seeing as Winrar is quite a cool program. I tried something called p7zip from Synaptic Package Manager, but it doesnt appear to have installed an actual program - I can't find it in /etc.

---

### Post by lykeion on 2010-11-01
Supposing you have installed the unrar package, you can extract the rar archive inside a jpeg image like this:
```
rar e image.jpg
```

And this is the way you'd embed a rar archive into an image:
```
cat original.jpg archive.rar > new_image.jpg
```

Note, it doesn't have to be an rar archive. You could also embed a zip archive with the same command, and use "unzip image.jpg" to extract it.

Most linux users would think doing this with simple command-line is way more cooler than any windows software.

EDIT
For a more complete steganography tool you can use steghide:
[http://justbored.wordpress.com/2007/12/27/steganography-and-linux-a-short-steghide-howto/](http://justbored.wordpress.com/2007/12/27/steganography-and-linux-a-short-steghide-howto/)

---

### Post by Legeril on 2010-11-01
Thanks I'll look into it :)

---

