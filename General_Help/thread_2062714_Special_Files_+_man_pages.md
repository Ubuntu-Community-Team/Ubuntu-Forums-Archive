---
title: "Special Files + man pages"
date: 2012-09-25
forum: General Help
---

### Post by matt1q23 on 2012-09-25
Hello All,

I am taking an Ubuntu class this semester and I am a bit confused about man pages and special files. The book that we are using for the class is based on the last LTS version of Ubuntu. I am using 12.04 LTS so I am aware that there are a few differences between versions.

The question that I am having an issue with goes as follows.

**"How many man pages are in the Devices subsection of the system manual? (Hint: Devices is a subsection of Special Fies.)"**


So I have been searching for info on this question online and have not been able to find a specific answer. 

I have tried running commands such as man man or man special files or man devices but have not really been able to find anything.

Can anyone point me to the correct answer? What is a special file? 

Thank you for the help.

---

### Post by gordintoronto on 2012-09-25
Have a look at this page:
[http://www.cyberciti.biz/faq/understanding-unix-linux-bsd-device-files/](http://www.cyberciti.biz/faq/understanding-unix-linux-bsd-device-files/)

A device is a "special file," and they live in /dev

What I don't understand is "system manual."

Oops, got it. Have a look at /usr/share/man/man4 which contains section 4 of the manpages.

---

### Post by matt1q23 on 2012-09-30
> **gordintoronto said:**
> Have a look at this page:
[http://www.cyberciti.biz/faq/understanding-unix-linux-bsd-device-files/](http://www.cyberciti.biz/faq/understanding-unix-linux-bsd-device-files/)

A device is a "special file," and they live in /dev

What I don't understand is "system manual."

Oops, got it. Have a look at /usr/share/man/man4 which contains section 4 of the manpages.

Thanks for the link very helpful information.


I have navigated to the location that you specified through the explorer, but I still don't know exactly what I am looking for..


Could you give any more details? I apologize for my ignorance, learning here.

---

### Post by JKyleOKC on 2012-09-30
That could be a very tricky question to answer. Section 4 of the man pages, on my system here, has entries for 73 devices. However I can install additional kinds of hardware, and that may well increase the number, while if I remove some of the pages that are not relevant to my system, it would be reduced. In other words, "How many?" is a question to which there is no universal correct answer!

---

### Post by gordintoronto on 2012-09-30
> **matt1q23 said:**
> I have navigated to the location that you specified through the explorer, but I still don't know exactly what I am looking for..

Your homework assignment could be restated as, "how many files are in /usr/share/man/man4".

When you ran: man man
it said that section 4 is devices.

However, as JKyleOKC pointed out, there is no universal answer. I have 62 files, he has 73.

---

