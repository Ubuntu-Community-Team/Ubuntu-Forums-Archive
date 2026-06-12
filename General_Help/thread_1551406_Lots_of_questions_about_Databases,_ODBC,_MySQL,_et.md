---
title: "Lots of questions about Databases, ODBC, MySQL, etc"
date: 2010-08-12
forum: General Help
---

### Post by Misterbadexample on 2010-08-12
Wordy explanation coming up, but bear with me, I am begging for sound advice from somebody knowledgeable on the subjects involved...

I have a couple of odd problems and I am in need of advice/explanations from somebody with understanding of Database programs/database servers/ODBC capable software, etc.

At my company we use some old accounting software from a company called Acclivity. It's pretty much the same thing as your typical accounting software like Quickbooks, except Quickbooks comes with some minor database program that runs on the host computer. The Acclivity software runs SLOOOOW over our network but Quickbooks runs very quickly. I assume it's because the Acclivity program runs through one huge monolithic file while Quickbooks has the database program. I could easily be wrong on this, though.

Anyway, as it turns out, the Acclivity program is ODBC capable and newer versions come with a Windows ODBC program that kind-of, sort-of works, from what I gather from the forums on the company website. They don't offer a lot of support and their website doesn't have great information. But I'm thinking that this will allow me to use some sort of OSS solution to host the file/database/etc and speed up performance of the software on the networked computers.

My questions are the following--what does this addition of ODBC capability likely offer me? Am I correct with my assumptions or am I wrong about all this?

How likely is it that I need a proprietary program to use this capability since ODBC is, well, "open?" Just what does ODBC mean and what should I be able to do with it? (I have looked this up on Wikipedia, but it opened up more questions than it answered.)

Is it likely I can use something like a MySQL program to host this database on an Ubuntu Server or Desktop system?

Is it likely to speed up the performance of this accounting software over my network?

Do I need an Ubuntu Server machine or will a Ubuntu Desktop machine do? What's the difference in the problems they're solving?

Have I given anywhere near enough information to answer these questions? I'm clearly over my head here as I'm no engineer and any help is definitely appreciated. I'll fill in any information needed to better understand the problems.

---

### Post by DaithiF on 2010-08-12
Hi,
When they say they support ODBC, what they almost certainly mean is that its possible to connect to their database using something other than their client software, e.g. you could connect a generic sql client and run database queries to extract data, or that a developer could write a script or application to connect & query and/or manipulate the data.  Think of ODBC as offering a bridge into their database.

But its unlikely that they mean what you have interpreted it as, ie. that their client software can be ported across various database backends, so long as those database backends support ODBC.  Applications that are 'database-agnostic' like this and that can be switched from one database platform backend to another are quite rare.

---

### Post by Misterbadexample on 2010-08-12
Let me see if I understand you correctly.

ODBC support means I could have an application created that gleans information from the file because it is an open standard. E.g., I could have a program that takes invoices and builds a calendar by the dates, or something like that, by taking information from the file.

And basically I have no hope of speeding up the file like I was hoping and wishing. The file is likely too proprietary to be hosted by some generic backend and do what the proprietary programs are looking for.

Not the answer I was hoping for, but I think you've helped me understand the meaning of the terms a little better. I suppose I can find the other minor information I need on my own. Thanks for helping. I see now I have a lot of work ahead of me to find the right solution to my issue.

---

### Post by DaithiF on 2010-08-12
yes, exactly.

good luck.

---

