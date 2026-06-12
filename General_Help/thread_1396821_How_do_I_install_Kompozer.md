---
title: "How do I install Kompozer?"
date: 2010-02-02
forum: General Help
---

### Post by AmirM on 2010-02-02
It might be not new,it might be answered many times earlier but....there are always newcomers!!
I searched a lot but i didnt find a good HOWTO for installing softwares from .tar.bz2 files(and.tar.gz).

---

### Post by rocket16 on 2010-02-02
What is the Software? Is it some theme? Then, you can do it directly, just by selectly it from the Login or Theme menu in each case.

---

### Post by AmirM on 2010-02-02
> **rocket16 said:**
> What is the Software? Is it some theme? Then, you can do it directly, just by selectly it from the Login or Theme menu in each case.
It's Kompozer.a software like Microsoft Frontpage for web design.

---

### Post by rocket16 on 2010-02-02
Else, Right click the package and select "Extract Here". And, in the new folder that is created, open and find a file with the likely name of "Install" or "Readme". There, the instruction will be given. Then, drop a shell, and enter "cd location" where location is the location of the folder, like "/home/user/desktop/folder". And, if there is any file like install.sh, then enter "./install.sh" after "./configure" and "./autogen.sh" if any. Else, you may try "./configure", then "make" and then "make install". These are called Binaries.

---

### Post by Robster2 on 2010-02-02
tar -xjvf filename.bz2

-j is bz2

---

### Post by AmirM on 2010-02-02
```
amir@Desktop:~/kompozer$ ./configure
bash: ./configure: No such file or directory
amir@Desktop:~/kompozer$ ./autogen.sh
bash: ./autogen.sh: No such file or directory
amir@Desktop:~/kompozer$ ./install.sh
bash: ./install.sh: No such file or directory

```

---

### Post by rocket16 on 2010-02-02
And, why don't you install the KompoZer using Add/Remove? Select Applications->Add/Remove. Then, in the search box, type "KompoZer", and when the Search results come, check the box beside "KompoZer". Then, select "Apply". Everything will be done automatically, then.

---

### Post by rocket16 on 2010-02-02
You may also open Applications->Accessories->Terminal, and enter exactly "sudo apt-get install kompozer", press enter, then enter your Password, and press enter. Then, it will be done automatically.

---

### Post by rocket16 on 2010-02-02
Oh, then the files aren't there. Then, do  it using the Terminal or Add/Remove, as I stated above.

---

### Post by Robster2 on 2010-02-02
If you are installing Komposer why did you not just install it from the Synaptic   (System>Administration>Synaptic Package Manager)?

It is much easier.

---

### Post by rocket16 on 2010-02-02
> **Robster2 said:**
> If you are installing Komposer why did you not just install it from the Synaptic   (System>Administration>Synaptic Package Manager)?

It is much easier.

Yes, but using Add/Remove is not hard too. Isn't it?

---

### Post by AmirM on 2010-02-02
I CAN install it from that Add/Remove function but I dont WANT.when I install it from there it doesnt work properly.when i open .ie INSERT and want to go down the menu the program closes.
I asked somwewhere else and they said its a problem with GTK and try to dowload a .tar.bz2 and install from there.

---

### Post by rocket16 on 2010-02-02
Then did you try "sudo apt-get install kompozer" command in the Shell?

---

### Post by AmirM on 2010-02-02
not yet.
downloading again?:?

is this difference between that apt command and Add/Remove?they dont use same repository?

---

### Post by aysiu on 2010-02-02
> **AmirM said:**
> I CAN install it from that Add/Remove function but I dont WANT.when I install it from there it doesnt work properly.when i open .ie INSERT and want to go down the menu the program closes.
I asked somwewhere else and they said its a problem with GTK and try to dowload a .tar.bz2 and install from there.
Maybe this will help:
[How to Open KompoZer When It Crashes Using Ubuntu (Linux)](http://hubpages.com/hub/KompoZer-Crashes-Ubuntu-Linux)

---

### Post by rocket16 on 2010-02-02
If you consider the Download, then it is really troublesome. But yo may try it once, in case you ignore additional download.

---

### Post by rocket16 on 2010-02-02
> **aysiu said:**
> Maybe this will help:
[How to Open KompoZer When It Crashes Using Ubuntu (Linux)]("http://hubpages.com/hub/KompoZer-Crashes-Ubuntu-Linux")

Thanks for your nice search, friend. I too, was trying to get one result like that. Thanks.

---

### Post by AmirM on 2010-02-02
> **aysiu said:**
> Maybe this will help:
[How to Open KompoZer When It Crashes Using Ubuntu (Linux)]("http://hubpages.com/hub/KompoZer-Crashes-Ubuntu-Linux")
  thanx that worked.:D

---

### Post by fab.head on 2010-02-02
A newer/stabler version can be downloaded from getdeb.net

[http://www.getdeb.net/updates/Ubuntu/9.10/?q=kompozer]("http://www.getdeb.net/updates/Ubuntu/9.10/?q=kompozer")

---

### Post by Robster2 on 2010-02-02
> **rocket16 said:**
> Yes, but using Add/Remove is not hard too. Isn't it?

Agreed,  It is the absolutely the same,  I probably started my post while you where writing yours.  

Why is the OP mucking around with tar when Komposer is in the repository?

Although this stuff is worth knowing for programs that are not in the repository.

---

### Post by Geweten on 2010-03-24
Hi guys !

I doubt this being completely solved... Since the Kompozer in Synaptics repositories is an unstable one dating from ubuntu 6...

I installed it and it crashes, as they state on the Kompozer downloadpage...

So maybe the untar-version is a stable one ?

Any ideas ?

Thx in advance ! ;)

---

### Post by Geweten on 2010-03-30
Ok I figured it out for me...  This was very useful...  [http://hubpages.com/hub/KompoZer-Crashes-Ubuntu-Linux](http://hubpages.com/hub/KompoZer-Crashes-Ubuntu-Linux)

---

