---
title: "001, 002, 003, etc archive help"
date: 2011-01-29
forum: General Help
---

### Post by COKEDUDE on 2011-01-29
Does anyone know of a program that can open 001, 002, 003, etc archives in Linux? The only program that I know of that can do this is 7-zip and there is no Linux package. I already tried p7zip with no luck.

---

### Post by zvacet on 2011-01-29
```
sudo apt-get install p7zip-full p7zip-rar
```

---

### Post by COKEDUDE on 2011-01-29
> **zvacet said:**
> ```
sudo apt-get install p7zip-full p7zip-rar
```

I have both of those programs. This is what happened. 

```
~ $ p7zip -d "/home/bob/Downloads/vid1.avi.001"
/usr/bin/p7zip: /home/bob/Downloads/vid1.avi.001 unknown suffix -- ignored
```

---

### Post by AlphaLexman on 2011-01-29
Check out [hjsplit]("http://www.hjsplit.org/linux/") there is a GUI and a CLI.

---

### Post by eddier on 2011-01-29
They are not archived files but split files. As per AlphaLexmans post you need HJSPLIT to join them. You will need need Sun Java to run it.

eddie

---

### Post by tkoco on 2011-01-29
> **COKEDUDE said:**
> Does anyone know of a program that can open 001, 002, 003, etc archives in Linux? The only program that I know of that can do this is 7-zip and there is no Linux package. I already tried p7zip with no luck.

In the Synaptic Package Manager, I found lxsplit which states that it is compatible with hjsplit files

---

### Post by COKEDUDE on 2011-01-30
> **tkoco said:**
> In the Synaptic Package Manager, I found lxsplit which states that it is compatible with hjsplit files

Yes you are correct. This does the trick. 

```
lxsplit -j  "/home/bob/Downloads/vid1.avi.001"
```

I also found out from reading file rollers wiki page that **7zip** uses the name **7z**. **7z** is also able to help. You can extract the video like this :). 

```
7z e "/home/bob/Downloads/vid1.avi.001"
```

[http://en.wikipedia.org/wiki/File_Roller](http://en.wikipedia.org/wiki/File_Roller)

---

### Post by COKEDUDE on 2011-02-14
I wanted to point out that if you are joining more than 10 files that you need to use a similar format to this. 

vid01.avi.001
vid02.avi.002
vid03.avi.003
vid04.avi.004
vid05.avi.005
vid06.avi.006
vid07.avi.007
vid08.avi.008
vid09.avi.009
vid10.avi.010

---

