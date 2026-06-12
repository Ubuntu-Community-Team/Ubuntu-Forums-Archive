---
title: "I need Help"
date: 2009-07-02
forum: General Help
---

### Post by keera on 2009-07-02
I just installed ubuntu 9.04 and am wondering if any one can help me to install amsn , unrar and give me a simple tuto on how to install adobe flash player 
thanks a lot

---

### Post by WRDN on 2009-07-02
Most things can be installed from the repositories (in this case, all things):

For amsn:

```
sudo apt-get install amsn
```

For adobe flash player:

```
sudo apt-get install flashplugin-nonfree
```

To unrar:

```
sudo apt-get install unrar
```

Install all at once, in a single command:

```
sudo apt-get install amsn flashplugin-nonfree unrar
```

Note, you may need to [add the Medibuntu repositories]("https://help.ubuntu.com/community/Medibuntu") to get some items.

---

### Post by benj1 on 2009-07-02
for flash, you need to install the 'ubuntu-restricted-extras' package, its in the repositories (synaptic), it also includes mp3 support etc.

a quick search and amsn and unrar is also.

go to system-->administration-->synaptic package manager
put your login password in. search for packages, right click mark for installation and the apply.

most programs you will want will be in the repositories, if you want something look there first.

---

### Post by keera on 2009-07-02
> **WRDN said:**
> Most things can be installed from the repositories (in this case, all things):

For amsn:

```
sudo apt-get install amsn
```For adobe flash player:

```
sudo apt-get install flashplugin-nonfree
```To unrar:

```
sudo apt-get install unrar
```Install all at once, in a single command:

```
sudo apt-get install amsn flashplugin-nonfree unrar
```Note, you may need to [add the Medibuntu repositories]("https://help.ubuntu.com/community/Medibuntu") to get some items.

when i put those code here is what i got

dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.

what should i do?

---

### Post by WRDN on 2009-07-02
Run the command the output requested:

```
sudo dpkg --configure -a
```

---

### Post by keera on 2009-07-02
> **benj1 said:**
> for flash, you need to install the 'ubuntu-restricted-extras' package, its in the repositories (synaptic), it also includes mp3 support etc.

a quick search and amsn and unrar is also.

go to system-->administration-->synaptic package manager
put your login password in. search for packages, right click mark for installation and the apply.

most programs you will want will be in the repositories, if you want something look there first.

sudo dpkg --configure -a after puting this code i did what u told me to do

and here is what i got :

W: Failed to fetch [http://tn.archive.ubuntu.com/ubuntu/pool/main/t/tk8.5/tk8.5_8.5.6-3_i386.deb](http://tn.archive.ubuntu.com/ubuntu/pool/main/t/tk8.5/tk8.5_8.5.6-3_i386.deb)
  Error writing to output file - write (28 No space left on device) [IP: 91.189.88.40 80]


W: Failed to fetch [http://tn.archive.ubuntu.com/ubuntu/pool/universe/t/tcltls/tcl-tls_1.5.0.dfsg-9_i386.deb](http://tn.archive.ubuntu.com/ubuntu/pool/universe/t/tcltls/tcl-tls_1.5.0.dfsg-9_i386.deb)
  Bad header line [IP: 91.189.88.40 80]


W: Failed to fetch [http://tn.archive.ubuntu.com/ubuntu/pool/universe/s/snack/libsnack2-alsa_2.2.10-dfsg1-8_i386.deb](http://tn.archive.ubuntu.com/ubuntu/pool/universe/s/snack/libsnack2-alsa_2.2.10-dfsg1-8_i386.deb)
  Bad header line [IP: 91.189.88.40 80]


W: Failed to fetch [http://tn.archive.ubuntu.com/ubuntu/pool/universe/a/amsn/amsn_0.97.2~debian-2ubuntu2_i386.deb]("http://tn.archive.ubuntu.com/ubuntu/pool/universe/a/amsn/amsn_0.97.2%7Edebian-2ubuntu2_i386.deb")
  Got a single header line over 360 chars [IP: 91.189.88.40 80]

any solutions??

---

### Post by Unforgivable on 2009-07-02
You could use Synaptic : click Alt+F2 then type synaptic
fill in the search box with whatever you're looking for, ex: amsn
then "check" it & it'll do the job for you

I did through sudo apt-get though.

---

### Post by keera on 2009-07-02
E: ERROR: could not create configuration directory /home/keera/.synaptic - mkdir (28 No space left on device)

here is what i got

:( any other solution for my problem pleaaaaaase

---

### Post by WRDN on 2009-07-02
> **keera said:**
> E: ERROR: could not create configuration directory /home/keera/.synaptic - mkdir (28 **No space left on device**)

here is what i got

:( any other solution for my problem pleaaaaaase

Have you got any storage left on the partition holding the home folder? According to the error, you haven't.

---

### Post by benj1 on 2009-07-02
how much space have you got on your hard drive/ partition ?

---

### Post by keera on 2009-07-02
52 g

---

### Post by Sef on 2009-07-02
Once you get that problem resolved.  They easy way to install them is check if they are in add/remove.

Applications > Add/Remove > Show: All Available applications > Search: Name_of_Application > repeat if searching for more than one application > (when finished with searching for applications) > click apply changes > apply > close

---

### Post by keera on 2009-07-02
and how can i resolve that problem
i tryed to do application==>add/remove
i see this msg after a while of loading :
This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

what should i do?

---

### Post by keera on 2009-07-02
can anyone help me please???

---

### Post by benj1 on 2009-07-02
type df -h in to your terminal, that will give you partition sizes and disk usage for your partitions, is there room on your main partition, it will be the one mounted on '/'.


if your hard drive is full, you either need to get rid of some stuff, or if its smaller than expected, it might have been miss sized at installation, you can use gparted on the live cd, but back up first.

if you have space then i would suggest what your pc suggests

sudo apt-get update' and 'sudo apt-get install -f'

(type them in the terminal, it will prompt for your password but won't echo anything while youre typing)

---

