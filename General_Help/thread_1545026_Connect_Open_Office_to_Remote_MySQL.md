---
title: "Connect Open Office to Remote MySQL"
date: 2010-08-03
forum: General Help
---

### Post by jonny75904 on 2010-08-03
This is not a new topic, I know that.  I am still so new to linux that most of the threads on this subject elude my understanding.  I'm getting there.

I'm using ubuntu 9.04.  I have several ecommerce websites and would like to be able to connect Open Office DIRECTLY to the site databases and do simple mail merging on envelopes. 

The problem is OO appears to be file based.  I read a thread suggesting to remove the Ubuntu version of OO and install directly from their site.  This is my problem:

There's no wizard.  

The readmes included in their archive speak to a more experienced crowd.  I THINK I'm just supposed to uninstall the existing one, then unzip the new OO to a folder?  That doesn't sound right though because that does not load dependencies.  

So, I have several questions in need of answering:

1.  Is a re-install really the correct way to access remote MySQL databases?  
2.  Would upgrading to 10.04 give me the ability?
3.  Can someone please give me a link for complete idiot's guide to OO installation on ubuntu?

Thanks,
Jonny

---

### Post by gordintoronto on 2010-08-03
I have a lot more experience than you do, and I don't know where I would begin in trying to solve the problem you have. Oh, yes I do: I would create a sysop-only web page which would dump the database on-screen into a format open-office spreadsheet would like, then I would cut-and-paste it onto my local computer. Not very elegant, but I know I could get it working pretty quickly -- and I wouldn't have to mess around with Open Office versions.

I have an enormous preference for sticking with the programs I can install using Synaptic. However, if you must get a later version of OO, use Synaptic to completely remove the current version, then go to the OO web site. Oh shucks, they do not provide a .deb file, which would be easy to install. Good luck with it.

I truly have no idea whether any version of OO would let you use a database which is part of a web site.

---

