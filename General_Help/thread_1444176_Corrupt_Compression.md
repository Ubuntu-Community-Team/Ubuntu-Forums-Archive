---
title: "Corrupt Compression"
date: 2010-03-31
forum: General Help
---

### Post by WinstonChurchill on 2010-03-31
I recently had a hard drive die and move on to more ferromagnetic pastures - luckily, I had foreseen this doom, and had been pretty religiously backing it up. However, the *.tar.gz file will not decompress. In Linux, I consistently get an error about "Unexpected EOF in archive", at which point TAR refuses to keep going, and in Windows, neither WinRAR or 7-Zip had anything else helpful to say (not that I expected they would)...

7-Zip gives me the following when I open the *.gz file in the "Archive Manager" and look at the properties on the *.tar file:
```
 Size:            131,106,816 Bytes
 Packed Size: 296,646,109,707 Bytes
```... which obviously doesn't make any sense. Something is amiss, but I'm quite certain all the data is there, and I'd like to recover as much of it as I can. I need a way to force this file to decompress and ignore errors - but the man page for the tar command in Linux doesn't seem to offer any way to do this, and neither do 7-Zip or WinRAR. My GPG Private Key is in there somewhere, so if all else fails I'd love to at least be able to get that back.

Any ideas? Thanks in advance!

---

### Post by john newbuntu on 2010-03-31
First try:
tar -tzvf filename.tar.gz
and see what it lists.

If you are lucky, say your filename ends with .pgp and is stored in directory "path"
tar -x path/*.pgp -zf filename.tar.gz
You could retrieve it that way.

Edit: If tar fails, I am sorry I do not know to recover the file.

---

### Post by WinstonChurchill on 2010-03-31
> **john newbuntu said:**
> First try:
tar -tzvf filename.tar.gz
and see what it lists.

If you are lucky, say your filename ends with .pgp and is stored in directory "path"
tar -x path/*.pgp -zf filename.tar.gz
You could retrieve it that way.

Edit: If tar fails, I am sorry I do not know to recover the file.

Thanks, but I've tried that: It extracts the entire directory tree, and then a handful of files, but it gets hung up before I see what I'm looking for.

---

### Post by john newbuntu on 2010-04-01
I assume your pgp file was not in what was listed. FYI, in future, when you tar a directory, always check the status of the tar using the command "echo $?" without the quotes and make sure it returns 0.
I'll defer this to someone else who can help you with this.

---

### Post by gmargo on 2010-04-01
> However, the *.tar.gz file will not decompress. In Linux, I consistently get an error about "Unexpected EOF in archive", at which point TAR refuses to keep going, and in Windows, neither WinRAR or 7-Zip had anything else helpful to say (not that I expected they would)You can test any *.gz file with "gzip -t name.gz".  If this test fails, then all bets are off regarding recovering the .tar file.

> but I'm quite certain all the data is thereWhy?

> and I'd like to recover as much of it as I can. I need a way to force this file to decompress and ignore errorsAbout the best you can do is
```

gzip -d < file.tar.gz | tar xfv -

```

---

### Post by WinstonChurchill on 2010-04-02
The *.tar.gz file is 273.6 GB, and when I attempt to extract it it spits out about 3 GB before it gives up - therefore I think it's safe to assume that there is something else there (How could you possibly end up with 265 GB of complete garbage?). I'm going to research the structure of gzip files and break out a hex editor and see what I can come up with...

Thanks for your suggestions.

---

