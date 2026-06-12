---
title: "Adobe Reader Read Aloud?"
date: 2010-04-23
forum: General Help
---

### Post by hawaiian1der on 2010-04-23
There is probably a thread already in the forums somewhere, but I'm blind as a bat when it comes to looking for things on the forums. In Winblows (>.<), you could make Adobe Reader read aloud the PDF. I have looked everywhere, added the medibuntu repositories, etc. Every website I have looked at said something including acroread. the acroread-plugins and the acroread-plugin-speech package. Even after following all of them I still cannot get to work. On another post in the forums it says I can only get it through Automatix, but when I Google it it mostly comes up with a program called Ultamatix. I installed it and there is no package in it that is the packages I need. Can anyone find out how to get those packages? Please and thank you.

---

### Post by hawaiian1der on 2010-04-23
Does anyone know? It is much easier to listen to something else read the text to me than reading it my self. I don't know why this is, but it is.

---

### Post by Chronon on 2010-04-23
I have never used this feature, but I have a "Read Out Loud" option in the View menu of Acrobat Reader 9.

---

### Post by ambdeep on 2010-04-23
just download adobe reader for linux from the official website.....it has the same features as the windows one.....

---

### Post by hawaiian1der on 2010-04-23
I did that second after deleting it after installing it from the Software Center. That didn't work.

---

### Post by hawaiian1der on 2010-04-25
Does anyone know?

---

### Post by hawaiian1der on 2010-04-27
I don't want to make a whole new thread... Does anyone know how to make this work on Ubuntu 9.10 Karmic? :confused:

---

### Post by hawaiian1der on 2010-04-28
Hello? Hello Computer? :P

---

### Post by hawaiian1der on 2010-05-02
Any one know how to make this happen in Lucid?

---

### Post by hawaiian1der on 2010-05-04
Does anyone know how to make this happen in Lucid?

---

### Post by djringjr on 2010-07-07
Hello - I am having the same problem - I haven't figured it out, but I found the Read Outloud command under the View menu - the first entry is Activate Read Outloud and then you have choices to read the current page or the whole document.

Right now, it has failed with ORCA running.

I am going to try [URL="http://mirrors.foxitsoftware.com/pub/foxit/reader/desktop/linux/1.x/1.1/enu/FoxitReader-1.1.0.tar.bz2"]Foxit Reader for Linux[/URL

In Windows Foxit had fast speed and worked well with screen reader.

You might join the www.vinux.org.uk email list.  You can contact the list owner here and he can add you to the list (avoids the GOTCHA visual problem).

vinux.development@googlemail.com[EMAIL="vinux.development@googlemail.com"]

If you go to that list, you'll have other people to help you.

Vinux is a distribution based on Ubuntu but optimized for those who are blind or visually impaired.

Best to you,

David Ring
Green Harbor, MA

-30-

---

### Post by djringjr on 2010-07-07
Also you might try turning off ORCA for a while - that's my next step.  I think Adobe's Read Out Loud might be configured to run from inside acrobat.

I don't know but I keep trying until I get something to work.

The work arounds we use are pdf to html conversion and then reading the html files.  That works very well but it is another stop and often means you have to use a pdf password cracker to convert the file as some files you cannot print.

They don't make it easy if you have eye impairment.

David

---

### Post by Mr_VeRiTy on 2010-09-21
Did anyone try running the windows version under wine? I'll try it now and post my results.

EDIT: Nope that didn't work for me :(, maybe there is another program that can read e-books aloud?

---

### Post by hawaiian1der on 2010-10-20
I am now in Maverick Meerkat and this option still doesn't work. It's not a dire situation, it's just that ti would make a little easier on me because I have ADD.... It's hard to sit and read a whole .pdf or even parts...

Please if anyone has found the solution, post the link here or explain

-Cameron Campos

---

### Post by vigyani on 2011-06-03
Hi 

I found a solution for Ubuntu 10.10 on the link below:

[https://bugs.launchpad.net/ubuntu/+source/acroread/+bug/741203]("https://bugs.launchpad.net/ubuntu/+source/acroread/+bug/741203")

Relevant portion reproduced:
> Read Out Loud

Adobe Reader has the ability to read text from PDF files out loud to the user. To enable Read Out Loud in Ubuntu please install the libgnome-speech7 package then run at the Terminal:

sudo /var/lib/dpkg/info/acroread.postinst configure

Open the desired PDF file and click View -> Read Out Loud -> Activate Read Out loud -> View -> Read Out Loud

and then choose either Read This Page Only or Read to End of Document.

Read Out Loud preferences are found by clicking Edit -> Preferences -> Reading

It worked for me.

Hope it helps.

---

