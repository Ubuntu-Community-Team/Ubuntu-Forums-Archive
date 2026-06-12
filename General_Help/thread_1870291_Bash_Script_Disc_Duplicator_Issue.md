---
title: "Bash Script Disc Duplicator Issue"
date: 2011-10-27
forum: General Help
---

### Post by Slayer706 on 2011-10-27
Hey everybody. I have very minimal experience with Linux, and no experience with bash scripting. I was looking for a DIY solution for making a disc duplicator, and this blog post caught my eye:
[http://blog.hackersare.us/2011/04/diy-dvd-duplicator-project-dvd-toaster.html](http://blog.hackersare.us/2011/04/diy-dvd-duplicator-project-dvd-toaster.html)

So I installed xubuntu on an older computer that I built from scratch for this particular project. I managed to follow the instructions and install SSH, then I set a manual IP and was able to remotely connect using PuTTY. :P

My problem lies with the script posted on that website (the first one, without the LightScribe code). I ran that script in an Ubuntu virtual machine to make sure it worked prior to constructing the duplicator and installing xubuntu on it. (I went with xubuntu since the duplicator has pretty low specs.) The script ran and worked in Ubuntu, but I am getting errors in xubuntu. I was hoping someone here would be able to tell me if I am missing something. I've already tried searching Google, which did not give me any relevant results for these particular errors.

These are the errors:
```
owner@owner-C51GM03:~/Desktop$ sh DiscDupeScript.sh
: not foundipt.sh: 2:
: not foundipt.sh: 3:
: not foundipt.sh: 4:
: not foundipt.sh: 5:
: not foundipt.sh: 6:
: not foundipt.sh: 7:
: not foundipt.sh: 8:
: not foundipt.sh: 9:
: not foundipt.sh: 10:
: not foundipt.sh: 11:
: not foundipt.sh: 12:
: not foundipt.sh: 13:
: not foundipt.sh: 14:
DiscDupeScript.sh: 31: Syntax error: word unexpected (expecting "}")
```

Any help would be greatly appreciated.

---

### Post by decoherence on 2011-10-27
those aren't useful errors. :( maybe a missing curly brace?

try running the script like this

> 
sh -x DiscDupeScript.sh


what does it say?

btw, you could do what the guy in the blog did and use ubuntu server instead of xubuntu. as long as you're only going to ssh in to it, ubuntu server is better for a low spec machine than xubuntu. ubuntu server does not have a GUI.

---

### Post by Slayer706 on 2011-10-27
> **decoherence said:**
> those aren't useful errors. :( maybe a missing curly brace?The script was presented on the blog as tested and working, which is why I am kind of bummed that it's not. Although it is kind of strange that I didn't get any errors when trying to run it in the Ubuntu VM (I didn't actually get to try to burn a disc in the VM though, the drives were all virtual).

> try running the script like this



what does it say?Well that does seem to be more descriptive. I'm not sure how to interpret the output though. My C#/C++ skills are useless when it comes to bash it seems. This is the output:```
owner@owner-C51GM03:~/Desktop$ sh -x DiscDupeScript.sh
+
: not foundipt.sh: 1:
+
: not foundipt.sh: 1:
+
: not foundipt.sh: 1:
+ dvd1=/dev/sr0
: not foundipt.sh: 1:
+
: not foundipt.sh: 1:
+ dvd2=/dev/sr1
: not foundipt.sh: 1:
+
: not foundipt.sh: 1:
+ dvd3=/dev/sr2
: not foundipt.sh: 1:
+
: not foundipt.sh: 1:
+ dvd4=/dev/sr3
: not foundipt.sh: 1:
+
: not foundipt.sh: 1:
+
: not foundipt.sh: 1:
+
: not foundipt.sh: 1:
DiscDupeScript.sh: 31: Syntax error: word unexpected (expecting "}")
```

Thanks for your help, by the way.> btw, you could do what the guy in the blog did and use ubuntu server instead of xubuntu. as long as you're only going to ssh in to it, ubuntu server is better for a low spec machine than xubuntu. ubuntu server does not have a GUI.I know that, but I haven't used any flavor of Linux for a very long time. I figured that I would need the GUI's help to do some of this stuff, and I didn't want to run Ubuntu on such a low spec machine. So I went with what the Ubuntu site described as a more lightweight alternative. Hopefully that wasn't a mistake.

---

### Post by decoherence on 2011-10-27
Could you copy/paste the script as it exists on the problematic xubuntu box? Also, could you try running it like this:

```
sh DiscDupeScript.sh 2> discdupe.err
```

That will redirect the error messages in to a file called discdupe.err where hopefully they'll be a bit more readable.

The script seems to work properly for me and I'm not even using an Ubuntu-based system. Might there be a typo or some formatting issue?

---

### Post by Slayer706 on 2011-10-27
> **decoherence said:**
> Could you copy/paste the script as it exists on the problematic xubuntu box? Also, could you try running it like this:

```
sh DiscDupeScript.sh 2> discdupe.err
```

That will redirect the error messages in to a file called discdupe.err where hopefully they'll be a bit more readable.

The script seems to work properly for me and I'm not even using an Ubuntu-based system. Might there be a typo or some formatting issue?I was actually already editing my reply when you posted... This is what I had wrote:

May have had a breakthrough here... I ran the script using this command:
```
owner@owner-C51GM03:~/Desktop$ bash DiscDupeScript.sh
```
And I got some errors that were actually understandable to me:
```
DiscDupeScript.sh: line 2: $'\r': command not found
DiscDupeScript.sh: line 3: $'\r': command not found
DiscDupeScript.sh: line 4: $'\r': command not found
DiscDupeScript.sh: line 5: $'\r': command not found
DiscDupeScript.sh: line 6: $'\r': command not found
DiscDupeScript.sh: line 7: $'\r': command not found
DiscDupeScript.sh: line 8: $'\r': command not found
DiscDupeScript.sh: line 9: $'\r': command not found
DiscDupeScript.sh: line 10: $'\r': command not found
DiscDupeScript.sh: line 11: $'\r': command not found
DiscDupeScript.sh: line 12: $'\r': command not found
DiscDupeScript.sh: line 13: $'\r': command not found
DiscDupeScript.sh: line 14: $'\r': command not found
DiscDupeScript.sh: line 31: syntax error near unexpected token `$'\r''
'iscDupeScript.sh: line 31: `    done
```

It seems like some invisible formatting characters might have went with the text that I copied and pasted from the blog. Once I deleted the whitespace around my first couple of lines, the number of errors decreased. So I continued doing that, until I am now stuck on this error:
```
DiscDupeScript.sh: line 104: syntax error near unexpected token `elif'
'iscDupeScript.sh: line 104: `    elif [ $copies -eq 3 -o $remaining -eq 2 ]
```
I'm pretty sure this is not an invisible character issue, since I have deleted/readded all of the whitespace on the surrounding lines.

You say that the script works for you though, so it must be a formatting problem... Perhaps you could post your working script as an attachment and I could try running it?

---

### Post by decoherence on 2011-10-27
Sure thing -- attached 

If you open the file in vi and type *:set list* you should be able to see any invisible characters.

---

### Post by Slayer706 on 2011-10-27
Well, I hit another snag. For some reason my xubuntu computer decided that it doesn't want to automatically mount flash drives anymore. I had to waste a CD on that 3kb file to get it over to the computer, but it seems to be working. I'm doing a test copy right now.

Here's the result of my test copy:
```
owner@owner-C51GM03:~/Desktop$ bash test.sh
Load DVD into top tray
Copying DVD to image
dd: reading `/dev/sr0': Input/output error
1222632+0 records in
1222632+0 records out
625987584 bytes (626 MB) copied, 144.78 s, 4.3 MB/s
How many copies?
1
test.sh: line 60: syntax error near unexpected token `elif'
test.sh: line 60: `    elif [ $copies -eq 3 -o $remaining -eq 2 ]'

```

So it made an image of the disc, but it error'd out when it got to the part where I was trying to burn a copy. I used vi and :set list, but I did not see any invisible characters around that particular line.

---

### Post by decoherence on 2011-10-27
the input/output error is a bit distressing but let's make the script run without an error before we jump to that issue.

please try running it with *bash -x* to get that extra output. I want to see why it's choking on line 60

thanks,

---

### Post by Slayer706 on 2011-10-27
> **decoherence said:**
> the input/output error is a bit distressing but let's make the script run without an error before we jump to that issue.

please try running it with *bash -x* to get that extra output. I want to see why it's choking on line 60

thanks,Okay, here is the result of that. It doesn't seem to give any extra info about the error. :(
```
+ '[' 0 -eq 0 ']'
++ grep -c 'blank: *0'
++ udisks --show-info /dev/sr0
+ dvd_load=0
+ '[' 0 -eq 0 ']'
++ grep -c 'blank: *0'
++ udisks --show-info /dev/sr0
+ dvd_load=1
+ '[' 1 -eq 0 ']'
+ echo 'Copying DVD to image'
Copying DVD to image
+ dd if=/dev/sr0 of=dvdimage.iso bs=512
dd: reading `/dev/sr0': Input/output error
1222632+0 records in
1222632+0 records out
625987584 bytes (626 MB) copied, 135.427 s, 4.6 MB/s
+ eject /dev/sr0
+ echo 'How many copies?'
How many copies?
+ read copies
1
+ count=1
test.sh: line 60: syntax error near unexpected token `elif'
test.sh: line 60: `    elif [ $copies -eq 3 -o $remaining -eq 2 ]'
owner@owner-C51GM03:~/Desktop$

```I couldn't get the initial output since that while loop that waits for you to insert a disc floods the console window.

As for the input/output error, it's possible that the DVD-ROM drive I am using is bad. I tested it by playing a DVD beforehand (which worked fine), but it could have some slight problems. That's no big deal though, I have a whole box full of them.

---

