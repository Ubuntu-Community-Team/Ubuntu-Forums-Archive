---
title: "installing TrueCrypt in ubuntu 9.10???"
date: 2010-04-21
forum: General Help
---

### Post by maxrpowell on 2010-04-21
I am trying to install TrueCrypt in ubuntu 9.10 and I am having troubles. When I to extract the tar.gz that the program comes in, I get this error: 
     'gzip: stdin: unexpected end of file
      tar: Unexpected EOF in archive
      tar: Error is not recoverable: exiting now'

The file also comes with a PGP file. (tar.gz.sig.). I am not sure how to use the signature file to open the archive. Any ideas? Here is the site I downloaded from: [http://www.truecrypt.org/downloads](http://www.truecrypt.org/downloads) 

Any help is appreciated. Thanks guys!

---

### Post by _0R10N on 2010-04-21
If the problem occurs when you're attempting to extract the file, then it may be a problem in the file you've downloaded. Try downloading it again. If the problem persists, then the original file is corrupt. If that happens, let me know and I upload the copy I've got, to some file server.

Kind regards!

_0R10N >>

---

### Post by screaminfakah on 2010-04-21
[http://ubuntuforums.org/showthread.php?t=1190053](http://ubuntuforums.org/showthread.php?t=1190053)

---

### Post by maxrpowell on 2010-04-21
Yes, the problem persists. Same error. All of the older releases have the same error also. I would appreciate if you would put it on a file server.

---

### Post by maxrpowell on 2010-04-21
[http://ubuntuforums.org/showthread.php?t=1190053](http://ubuntuforums.org/showthread.php?t=1190053) <-- doesn't work

---

### Post by _0R10N on 2010-04-21
:( ok!

AMD64 or 32???

Kind regards!

_0R10N >>

---

### Post by maxrpowell on 2010-04-21
32

---

### Post by _0R10N on 2010-04-21
Before trying anything else, look for it in your repos. If it isn't there, add the repo proposed on [www.apt-get.org](www.apt-get.org)


_0R10N >>

---

### Post by meho_r on 2010-04-21
Interesting, for some reason, there's no more .deb file for download :?

---

### Post by bwitherell on 2010-04-21
I was able to download and extract the setup file fine 2 min ago. Can you post the command you are using to extract the file?

---

### Post by _0R10N on 2010-04-21
You should try```
tar -xvf <truecrypt_file.tar.gz>
```

_0R10N >>

---

