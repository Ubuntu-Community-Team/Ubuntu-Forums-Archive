---
title: "Folder /usr/lib64 doesn't found"
date: 2012-09-21
forum: General Help
---

### Post by ArchGabriel on 2012-09-21
Hi guys,

I need to install libglut.so.3 in my Ubuntu 12.04 64 bits, so I did:

sudo apt-get install freeglut3 freeglut3-dev

Everything seems to work fine until  I get the following message: Missing libglut.so library.

So, I tried this:

sudo ls -s /usr/lib64/libglut.so.3 /usr/lib/libglut.so

Still got the same message, than I figured out that the folder /usr/lib64 doesn't exist! I tried

cd /usr/lib64

and I got a message saying that the folder doesn't exist! :shock:

Can anyone here help me please?

Thanks in advance,

---

### Post by spjackson on 2012-09-21
The freeglut3 package provides 
```

/usr/lib/libglut.so.3
/usr/lib/libglut.so.3.9.0

``` [http://packages.ubuntu.com/precise/amd64/freeglut3/filelist](http://packages.ubuntu.com/precise/amd64/freeglut3/filelist)

Why do you want a /usr/lib64 directory?

What is reporting "Missing libglut.so library"? Is that apt-get install?

---

### Post by ArchGabriel on 2012-10-04
I am trying to install CUDA Samples on my Ubuntu 12.04. 
Everything goes fine, until I try to install the CUDA Samples; I can install the drivers, SDK but not the samples.

---

### Post by ArchGabriel on 2012-10-04
> **spjackson said:**
> The freeglut3 package provides 
```

/usr/lib/libglut.so.3
/usr/lib/libglut.so.3.9.0

``` [http://packages.ubuntu.com/precise/amd64/freeglut3/filelist](http://packages.ubuntu.com/precise/amd64/freeglut3/filelist)

Why do you want a /usr/lib64 directory?

What is reporting "Missing libglut.so library"? Is that apt-get install?

In fact, I tried "/usr/lib/lobglut.so.3" and it returns: "No such file or directory".

---

### Post by mikewhatever on 2012-10-04
You can look for it with 'locate freeglut3', ...may need to run 'sudo updatedb' first.

---

### Post by spjackson on 2012-10-05
> **ArchGabriel said:**
> In fact, I tried "/usr/lib/lobglut.so.3" and it returns: "No such file or directory".
Interesting. The package contents at the link I quoted says /usr/lib/libglut.so.3, as does apt-file list freeglut3. However on my 64-bit Lubuntu 12.04 it is in /usr/lib/x86_64-linux-gnu/libglut.so.3. I don't know why there is this apparent discrepancy.

---

### Post by xwid on 2013-05-18
I had similar problem, even if there was libglut.so in usr/lib folder. 

my solution was 
cp /usr/lib/libglut.so . 

sudo ln -s /usr/lib/x86_64-linux-gnu/libglut.so libglut.so

---

