---
title: "Cannot unrar"
date: 2009-07-10
forum: General Help
---

### Post by Captain_Falafel on 2009-07-10
I'm a n00b and I recently installed a program that required rar version 2.71. I think by installing it, it broke my ability to unrar some files. Whenever I hit extract on a .rar file, it starts to extract, but then exists the progress window. These are the commands I used to install rar 2.71, how can I uninstall it, or is there another way to get extracting working?

```
chmod +x rarlnx271.sfx.bin
./rarlnx271.sfx.bin
```

```
sudo chown -R root:root rar
sudo mv rar /usr/local/rar2.71
cd /usr/local/bin
ln -s /usr/local/rar2.71/rar .
ln -s /usr/local/rar2.71/unrar .
```

---

### Post by michy99 on 2009-07-10
When you say it required rar 2.71, do you mean it required that exact version, or that it required that version or later? I ask because the version in the repository is 3.80. Have you tried installing that version?```
 sudo apt-get install rar unrar
```

---

### Post by wojox on 2009-07-10
Use:

```
apt-get --purge remove rar2.71
```

---

### Post by Captain_Falafel on 2009-07-10
> **michy99 said:**
> When you say it required rar 2.71, do you mean it required that exact version, or that it required that version or later? I ask because the version in the repository is 3.80. Have you tried installing that version?```
 sudo apt-get install rar unrar
```


it suggested that version, but the max it said was 2.99.
the program was dvdrip
```
sudo apt-get install dvdrip rar
```
I've uninstalled, reinstalled, uninstalled that command, still nothing.
I had the latest version of rar, but when I tried ripping a dvd, it suggested rar2.71. However, it still didn't work. But, then when I tried to unrar a regular rar, it doesn't work anymore. 

and for some reason, when I do what wojax said, I get:
```
$ sudo apt-get --purge remove rar2.71
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package rar2.71

```

It might be something other than installing rar2.71, but I have no way of finding out what.
Thanks for your responses.

---

### Post by Jebtrix on 2009-07-11
I actually had better luck with the p7zip-rar package.. go figure

sudo apt-get install p7zip-rar

---

### Post by moster on 2009-07-11
There is no sense in asking for specific version of rar. It could only ask for MINIMAL version and up.

If you torture yourself enough, download newest winrar form home page, and install it right into ubuntu. Install wine first if yo do not have it.

If you cannot do it with winrar you have some other problem. And if winrar solve your problem, then try to figure what happend.

---

### Post by jerome1232 on 2009-07-11
> **Captain_Falafel said:**
> I'm a n00b and I recently installed a program that required rar version 2.71. I think by installing it, it broke my ability to unrar some files. Whenever I hit extract on a .rar file, it starts to extract, but then exists the progress window. These are the commands I used to install rar 2.71, how can I uninstall it, or is there another way to get extracting working?

```
chmod +x rarlnx271.sfx.bin
./rarlnx271.sfx.bin
```

```
sudo chown -R root:root rar
sudo mv rar /usr/local/rar2.71
cd /usr/local/bin
ln -s /usr/local/rar2.71/rar .
ln -s /usr/local/rar2.71/unrar .
```


based on that it lookes like you have that version of rar in /usr/local/bin and symlinks in /usr/local/rar2.71/rar and /usr/local/rar2.71/unrar.

You just need to remove those symnlinks and the binary file but

Before I go giving delete commands I'd like to check and make sure everything is the way I think it is, can you post the output of...

```
ls /usr/local/bin/rar2.71
ls /usr/local/rar2.71/rar
ls /usr/local/rar2.71/unrar
```

---

### Post by CatKiller on 2009-07-11
Symlinks **to** /usr/local/rar2.71/rar and /usr/local/rar2.71/unrar.

```
ls /usr/bin/rar
ls /usr/bin/unrar
```

---

### Post by Captain_Falafel on 2009-07-11
> **jerome1232 said:**
> based on that it lookes like you have that version of rar in /usr/local/bin and symlinks in /usr/local/rar2.71/rar and /usr/local/rar2.71/unrar.

You just need to remove those symnlinks and the binary file but

Before I go giving delete commands I'd like to check and make sure everything is the way I think it is, can you post the output of...

```
ls /usr/local/bin/rar2.71
ls /usr/local/rar2.71/rar
ls /usr/local/rar2.71/unrar
```

Here are the results:
```
$ ls /usr/local/bin
[COLOR="DeepSkyBlue"]rar  unrar[/COLOR]

$ ls /usr/local/rar2.71
[COLOR="Lime"]default.sfx  rar [/COLOR]          rar.txt       rereg.txt
dos.sfx      rar_faq.txt   readme.txt    technote.txt
file_id.diz  rarfiles.lst  register.frm  [COLOR="Lime"]unrar[/COLOR]
license.txt  rar_site.txt  register.txt  whatsnew.txt

$ ls /usr/local/rar2.71/rar
[COLOR="Lime"]/usr/local/rar2.71/rar[/COLOR]

$ ls /usr/local/rar2.71/unrar
[COLOR="Lime"]/usr/local/rar2.71/unrar[/COLOR]

```


> Symlinks to /usr/local/rar2.71/rar and /usr/local/rar2.71/unrar.

```
ls /usr/bin/rar
ls /usr/bin/unrar
```



Results:
```
$ ls /usr/bin/rar
[COLOR="Lime"]/usr/bin/rar[/COLOR]

$ ls /usr/bin/unrar
[COLOR="DeepSkyBlue"]/usr/bin/unrar[/COLOR]

```


> There is no sense in asking for specific version of rar. It could only ask for MINIMAL version and up.

It asked for a range from a min to a max, and the max wasn't the latest version.

---

### Post by jerome1232 on 2009-07-11
well removing unrar2.71 should be a simple matter of removing those files then. I would make sure rar and unrar aren't installed from apt-get, remove your unrar/rar that you installed, then reinstall rar and unrar from apt-get. Hopefully that'll work.


```
sudo -i
apt-get remove rar unrar
rm /usr/local/bin/rar
rm /usr/local/bin/unrar
rm -r /usr/local/rar2.71
apt-get install rar unrar
exit
```

---

### Post by Captain_Falafel on 2009-07-11
> **jerome1232 said:**
> well removing unrar2.71 should be a simple matter of removing those files then. I would make sure rar and unrar aren't installed from apt-get, remove your unrar/rar that you installed, then reinstall rar and unrar from apt-get. Hopefully that'll work.


```
sudo -i
apt-get remove rar unrar
rm /usr/local/bin/rar
rm /usr/local/bin/unrar
rm -r /usr/local/rar2.71
apt-get install rar unrar
exit
```


worked like a charm! thanks for the responses! :popcorn:

---

### Post by Captain_Falafel on 2009-07-11
One last question.. how do I add a [SOLVED] title to this thread?

---

### Post by jerome1232 on 2009-07-11
It's under thread tools towards the upper right portion of the page. :)

---

### Post by Captain_Falafel on 2009-07-11
> **jerome1232 said:**
> It's under thread tools towards the upper right portion of the page. :)


I get these options only:

Thread Tools :
Show Printable Version 
Email this Page 
Subscribe to this T**[B]hread **[/B]
Add a Poll to this Thread

---

### Post by jerome1232 on 2009-07-11
odd, in that case edit your op, then hit edit again and you can edit the title.

---

