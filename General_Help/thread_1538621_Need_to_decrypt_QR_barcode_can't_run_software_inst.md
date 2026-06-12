---
title: "Need to decrypt QR barcode: can't run software installed via  ubuntu  repo"
date: 2010-07-25
forum: General Help
---

### Post by Melotten on 2010-07-25
Hi all! I have a Qr barcode to decrypt and to do this I installed from the official ubuntu repo the software needed. 
The problem is this: I can't see the software in any menu. 
From shell I know how to create a Qr barcode,  but I'm unable to decrypt one.
Someone have any idea about how to do it from  CLI or in any other way?

Thanks!

---

### Post by ks07 on 2010-07-25
What software did you install? I don't see any in the repos for decrypting... You could try typing in the name of the program you installed in a terminal and see what happens.

What I think you've done is downloaded libdecodeqr - which is a library, not a program. There may be some software which can use this somewhere on the internet. Otherwise, there are some QR decoding websites, such as this one: [http://zxing.org/w/decode.jspx](http://zxing.org/w/decode.jspx) that might work for you. :)

EDIT: Try the libdecodeqr-examples package, it says it contains a sample program which you may be able to use. (It's probably only available as source code though, so unless you have some experience with coding then that's probably a lost cause...

EDIT2: Best solution I have found so far is this sourceforge project: [http://pyqrcode.sourceforge.net/](http://pyqrcode.sourceforge.net/) The page contains full instructions on how to install and use it. :)

---

### Post by Melotten on 2010-07-25
Thanks a mil for your answer! Yes, the pCkage I installed is the one you indicated. 
I installed as well the example program and i tried to run it via shell, but the command as been not recognised.
I will try the web solution you indicated me, really thanks for your time!

P.S:
have you tried to run the package on your own? To do it I shoul locate the source and compile it as usual right?
Sorry the newbie questions mate, I'm trying to improve :)

---

### Post by ks07 on 2010-07-26
> **Melotten said:**
> Thanks a mil for your answer! Yes, the pCkage I installed is the one you indicated. 
I installed as well the example program and i tried to run it via shell, but the command as been not recognised.
I will try the web solution you indicated me, really thanks for your time!

P.S:
have you tried to run the package on your own? To do it I shoul locate the source and compile it as usual right?
Sorry the newbie questions mate, I'm trying to improve :)
I haven't tried the package myself sorry, but I think if you do find the source you should be able to compile it. I don't know how usable the outcome will be, as I don't know how complete an example it is. ;)

---

### Post by Melotten on 2010-07-26
To be homest, I found more quick and complete rhe websites I found around.
Actually I think something a bit more concrete should be implemented in an operative system like linux, this would make it more complete and easy to use.

Btw, the QR barcodes are cooooool!

Thanks a lot m8!

---

### Post by ks07 on 2010-07-27
> **Melotten said:**
> To be homest, I found more quick and complete rhe websites I found around.
Actually I think something a bit more concrete should be implemented in an operative system like linux, this would make it more complete and easy to use.

Btw, the QR barcodes are cooooool!

Thanks a lot m8!
I guess it's just not 'big' enough for someone to actually code and make a decoder with all the online tools, especially seeing as they're meant to be scanned while out and about and Ubuntu is meant for the desktop...

But who knows, if the library's there, then the chances are we'll see a qrdecode package in the repos one day soon. :p

EDIT: Looks like the libqrdecode-examples package is a lot better than I thought! You caught my interest so I had to download it for myself and I'm glad to say it works almost perfectly. To decode qr barcodes on ubuntu, first download [apt:libdecodeqr-examples](apt:libdecodeqr-examples) by clicking the link. Then to run the program, use the following:
```
libdecodeqr-simpletest /path/to/qr/barcode/file.picture
```
There is also libdecodeqr-webcam, but I have not tried it as I do not have a webcam!

---

### Post by Melotten on 2010-07-27
Hi!
well I'm trying to figure out how to do it, now is a sort of challenge! to use an online service was just a workaround and I'm actually very happy to caught you interest. is a very good tecnology actually and I think should me more diffused. but, coming back to our QR codes, I tried to clic on the link and I get a windows that is asking me with what I should open the link, and I don't really know what to select :D
I tried to run an apt-get with the name of the package  you indicated, but no luck, I get an "invalid operation".
I installed from the ubuntu software center the packages inside the repo, that are libdecodeqr0 - libdecodeqr-dev and libdecodeqr-examples, I tried to run the same command with the name of those libraries but, no luck. Was an attempt :)

any indication about how to proceed now?
thanks for your time, I' really appreciate that :)

---

### Post by ks07 on 2010-07-27
> **Melotten said:**
> Hi!
well I'm trying to figure out how to do it, now is a sort of challenge! to use an online service was just a workaround and I'm actually very happy to caught you interest. is a very good tecnology actually and I think should me more diffused. but, coming back to our QR codes, I tried to clic on the link and I get a windows that is asking me with what I should open the link, and I don't really know what to select :D
I tried to run an apt-get with the name of the package  you indicated, but no luck, I get an "invalid operation".
I installed from the ubuntu software center the packages inside the repo, that are libdecodeqr0 - libdecodeqr-dev and libdecodeqr-examples, I tried to run the same command with the name of those libraries but, no luck. Was an attempt :)

any indication about how to proceed now?
thanks for your time, I' really appreciate that :)
You need to be using firefox and have apturl installed for that to work. Should work out of the box, but no worry.

Anyway, the package you want is libdecodeqr-examples. Then you can try the example by using ```
libdecodeqr-simpletest /path/to/qr/barcode/file
``` it worked on a clean image from a web page as well as one in a photograph, although it does have to be quite large and clear. It doesn't seem to like the one you posted here though lol...

You may also try libdecodeqr-webcam, but I don't have a webcam to test it. :p

---

