---
title: "update manager and synaptic problems after power cut"
date: 2010-03-22
forum: General Help
---

### Post by benrufus on 2010-03-22
Hi

I just had a power cut whilst installing updates on my laptop (which dosen't have a battery) 

When i try to use update manager or synaptic now i get this message:

[B]E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
[/B]
when i do **sudo dpkg --configure -a **this is what i get:

[B]ubuntu@ubuntu:~$ sudo dpkg --configure -a
dpkg: parse error, in file `/var/lib/dpkg/updates/0198' near line 1:
 MSDOS EOF (^Z) in field name `
ubuntu@ubuntu:~$ [/B]

please help!!!!!!!!!!! i have nearly no idea what i'm doing in the terminal or what to do next.......

thanks

---

### Post by Enigmapond on 2010-03-22
I would check in Synaptic for broken installations, (custom tab on the left & broken on top). Un-install any you find and just repeat the update process. It's a thought anyway..:)

---

### Post by benrufus on 2010-03-22
> **Enigmapond said:**
> I would check in Synaptic for broken installations, (custom tab on the left & broken on top). Un-install any you find and just repeat the update process. It's a thought anyway..:)


yeah i thought about trying that. the problem is i cant get past the error box when i open synaptic. it says  

[B]An error occurred

The following details are provided:[/B]  as the box title 

and then inside the box

[B] E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.[/B]

i can't get past this box to use synaptic to try and fix any broken packages. when i close it it just closes synaptic.

thanks

---

### Post by plucky on 2010-03-22
> when i do sudo dpkg --configure -a this is what i get:

ubuntu@ubuntu:~$ sudo dpkg --configure -a
dpkg: parse error, in file `/var/lib/dpkg/updates/0198' near line 1:
MSDOS EOF (^Z) in field name `
ubuntu@ubuntu:~$

please help!!!!!!!!!!! i have nearly no idea what i'm doing in the terminal or what to do next.......

Open a terminal and ```
cd /var/lib/dpkg/updates/
ls
```

and see what files are there.Delete them using ```
sudo rm <name of file>
```

Then run ```
sudo apt-get update
``` and see what happens.

Post any errors to the forum.

Good Luck

---

### Post by benrufus on 2010-03-22
> **plucky said:**
> Open a terminal and ```
cd /var/lib/dpkg/updates/
ls
```and see what files are there.Delete them using ```
sudo rm <name of file>
```Then run ```
sudo apt-get update
``` and see what happens.

Post any errors to the forum.

Good Luck


thanks plucky! here is what i get:

[B]ubuntu@ubuntu:~$ cd /var/lib/dpkg/updates/
ubuntu@ubuntu:/var/lib/dpkg/updates$ ls
0000  0016  0032  0048  0064  0080  0096  0112  0128  0144  0160  0176  0192
0001  0017  0033  0049  0065  0081  0097  0113  0129  0145  0161  0177  0193
0002  0018  0034  0050  0066  0082  0098  0114  0130  0146  0162  0178  0194
0003  0019  0035  0051  0067  0083  0099  0115  0131  0147  0163  0179  0195
0004  0020  0036  0052  0068  0084  0100  0116  0132  0148  0164  0180  0196
0005  0021  0037  0053  0069  0085  0101  0117  0133  0149  0165  0181  0197
0006  0022  0038  0054  0070  0086  0102  0118  0134  0150  0166  0182  0198
0007  0023  0039  0055  0071  0087  0103  0119  0135  0151  0167  0183  tmp.i
0008  0024  0040  0056  0072  0088  0104  0120  0136  0152  0168  0184
0009  0025  0041  0057  0073  0089  0105  0121  0137  0153  0169  0185
0010  0026  0042  0058  0074  0090  0106  0122  0138  0154  0170  0186
0011  0027  0043  0059  0075  0091  0107  0123  0139  0155  0171  0187
0012  0028  0044  0060  0076  0092  0108  0124  0140  0156  0172  0188
0013  0029  0045  0061  0077  0093  0109  0125  0141  0157  0173  0189
0014  0030  0046  0062  0078  0094  0110  0126  0142  0158  0174  0190
0015  0031  0047  0063  0079  0095  0111  0127  0143  0159  0175  0191
ubuntu@ubuntu:/var/lib/dpkg/updates$ 
[/B]

that's a lot to delete, does this seem right? i'm getting nervous!!!!! hahaha

thanks

---

### Post by plucky on 2010-03-22
That directory is normally empty so it needs to be emptied and then you need to run the updates again.

You could ```
sudo rm *
``` as long as you are in that directory,to remove all those files at once.Just make sure you are in the correct directory.

Then run ```
sudo apt-get update
sudo apt-get upgrade
``` to restart the update process.

Good Luck

---

### Post by benrufus on 2010-03-22
> **plucky said:**
> That directory is normally empty so it needs to be emptied and then you need to run the updates again.

You could ```
sudo rm *
``` as long as you are in that directory,to remove all those files at once.Just make sure you are in the correct directory.

Then run ```
sudo apt-get update
sudo apt-get upgrade
``` to restart the update process.

Good Luck


thanks for you help Plucky!! those instructions worked perfectly!

---

### Post by Radioactivekid on 2011-07-28
Thank  you plucky!!!!!:popcorn:

---

### Post by Some One Here on 2012-12-23
Mr. plucky
thanks alot :)

---

