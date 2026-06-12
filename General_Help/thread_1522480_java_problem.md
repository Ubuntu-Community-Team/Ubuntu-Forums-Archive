---
title: "java problem"
date: 2010-07-02
forum: General Help
---

### Post by Oolongtea on 2010-07-02
```
deb http://archive.canonical.com/ lucid partner]
```

```
sudo apt-get update
```

```
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
```

I tried the steps above and when I entered the 3rd step I get this from the terminal:

Package sun-java6-jre is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-jre has no installation candidate



Any help would be greatly appreciated 

Thanks

---

### Post by doixanh on 2010-07-02
Try openjdk. sun java is not maintained anymore. :D

---

### Post by philinux on 2010-07-02
> **Oolongtea said:**
> ```
deb http://archive.canonical.com/ lucid partner]
```

```
sudo apt-get update
```

```
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
```

I tried the steps above and when I entered the 3rd step I get this from the terminal:

Package sun-java6-jre is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-jre has no installation candidate



Any help would be greatly appreciated 

Thanks

Sun java is available from the partner repo.

System>admin>software sources>Click the Other Software tab and tick partner.

Then you can install your packages.

---

### Post by Oolongtea on 2010-07-02
these set of codes have worked for me on other computers so I'm wondering whats up with this? Can anyone tell me?

---

### Post by philinux on 2010-07-02
> **Oolongtea said:**
> these set of codes have worked for me on other computers so I'm wondering whats up with this? Can anyone tell me?

See post #3. ;)

---

### Post by Oolongtea on 2010-07-02
I did that and I get this from software sources:


The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch [http://archive.canonical.com/dists/lucid/Release](http://archive.canonical.com/dists/lucid/Release)  Unable to find expected entry  partner]/binary-i386/Packages in Meta-index file (malformed Release file?)
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by philinux on 2010-07-02
> **Oolongtea said:**
> I did that and I get this from software sources:


The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch [http://archive.canonical.com/dists/lucid/Release](http://archive.canonical.com/dists/lucid/Release)  Unable to find expected entry  partner]/binary-i386/Packages in Meta-index file (malformed Release file?)
Some index files failed to download, they have been ignored, or old ones used instead.

Try changing the server in Software Sources, Try Main.

---

### Post by Leppie on 2010-07-02
i'm not sure if this was a typo in your post, or it's the real entry in your sources.list:
> **Oolongtea said:**
> ```
deb http://archive.canonical.com/ lucid partner[COLOR=Red]**]**[/COLOR]
```
this should be:
```
deb http://archive.canonical.com/ lucid partner
```

---

### Post by Oolongtea on 2010-07-02
didn't work...I received the same message as before.

---

### Post by Leppie on 2010-07-02
could you post the result of the following command:
```
apt-cache search sun java runtime
```

and did you run apt-get update again after modifying sources.list?

---

### Post by Oolongtea on 2010-07-02
It runs smoothly now! Thanks for your guys help. Should of seen the spelling error...my bad.

---

### Post by Leppie on 2010-07-02
may i ask you what you did exactly to solve this?
your solution might help others as well ;)

---

### Post by Oolongtea on 2010-07-02
more like your solution! it was that spelling error you pointed out. I kinda feel idiotic for not noticing it.

---

### Post by Leppie on 2010-07-02
ok cool, glad it worked.
don't feel idiotic about it, these things are easy to miss ;)

---

