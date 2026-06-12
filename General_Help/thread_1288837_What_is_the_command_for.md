---
title: "What is the command for"
date: 2009-10-11
forum: General Help
---

### Post by BigCityCat on 2009-10-11
making a directory $HOME/.mozilla/plugins

---

### Post by OpenGuard on 2009-10-11
```
mkdir $HOME/.mozilla/plugins
```

---

### Post by BigCityCat on 2009-10-11
okay it says it already exists but thanks.

---

### Post by BigCityCat on 2009-10-11
can you tell me how to extract a tar file to that directory

---

### Post by cdwillis on 2009-10-11
Open your archive then select where you'd like to extract it, when the list of folders comes up press ctrl-h and you should be able to see the hidden folders. Navigate to ~/.mozilla/plugins and you're set.

---

### Post by OpenGuard on 2009-10-11
```
tar -xvf filename.tar
```

After that, if everything looks good, move it with:
```
mv /source/folder /target/folder
```

---

### Post by BigCityCat on 2009-10-11
okay I did this with no output is this right

paul@paul-laptop:~/Desktop$ tar -xvf libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
libflashplayer.so
paul@paul-laptop:~/Desktop$ mv libflashplayer.so $HOME/.mozilla/plugins
paul@paul-laptop:~/Desktop$

---

### Post by OpenGuard on 2009-10-11
> **BigCityCat said:**
> okay I did this with no output is this right

paul@paul-laptop:~/Desktop$ tar -xvf libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
libflashplayer.so
paul@paul-laptop:~/Desktop$ mv libflashplayer.so $HOME/.mozilla/plugins
paul@paul-laptop:~/Desktop$

Yes, tough, I don't get it .. why didn't you just installed flashplugin-nonfree ?

---

### Post by cdwillis on 2009-10-11
The version from the website might be newer than the version in the repository for him, like if he's using Hardy.

---

### Post by BigCityCat on 2009-10-11
for some reason it doesn't work completely. It works but I have some issues with flash. It's installed but if I goto adobes website to check it it says install missing plugin. I am using a 64bit version of firefox. shockwave is installed. If I goto aol games and try to play spades it wont work but If I goto view some flash it does. So I don't know what to do.

---

### Post by BigCityCat on 2009-10-11
could adblock be messing me up?

---

### Post by jeremyswalker on 2009-10-11
The command should be ```
tar -xvzf filename.tar.gz
``` because the file is gzipped.

---

### Post by BigCityCat on 2009-10-11
> **jeremyswalker said:**
> The command should be ```
tar -xvzf filename.tar.gz
``` because the file is gzipped.

Yeh thats what I did. Thanks though.

---

### Post by BigCityCat on 2009-10-11
cant get this to work

[http://www.games.com/game/spades](http://www.games.com/game/spades)

but can get this

[http://web.mlsnet.com/index.jsp](http://web.mlsnet.com/index.jsp)

---

### Post by OpenGuard on 2009-10-11
> **BigCityCat said:**
> cant get this to work

[http://www.games.com/game/spades](http://www.games.com/game/spades)

but can get this

[http://web.mlsnet.com/index.jsp](http://web.mlsnet.com/index.jsp)


Spades are in Java, not Flash.

```
sudo apt-get install sun-java6-jre sun-java6-plugin
```

---

### Post by BigCityCat on 2009-10-11
okay then I have all that but since 64 bit java is hit or miss then I guess this site is a miss, but this other person said he had that site working with chromium 64 bit.

---

