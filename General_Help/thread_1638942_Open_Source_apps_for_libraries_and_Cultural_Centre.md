---
title: "Open Source apps for libraries and Cultural Centre ?"
date: 2010-12-06
forum: General Help
---

### Post by Bartje on 2010-12-06
Hi,

I currently have 2 jobs, in the same village in Belgium, more specifically in the library and in the cultural centre of the village.

The ICT Manager has no clue about open source, and some of the applications we use are ridiculously expensive and way overkill for a little village as where I work. I would like to suggest a couple of changes, to cut costs, and simplify things. I'll explain and separate my questions in two parts.

1. Library
In the library there are 3 computers for searching our collection. These are now windows based machines, with a WinU interface that limit the options of the computer usage to a web browser that only shows the catalogue. 
I personally find it ridiculous that we have to pay licenses for simply browsing and a license for limiting the computer usage.
What I now would like to suggest is to switch to Linux (most probably Ubuntu), and limit the user rights to the usage of that one web page in the browser, which should load on start up.
My question now is, how do I achieve this? Is there an open source linux app that does the same thing as WinU or do I have to configure user rights in some way that gives me the same result? If so, how do I do this?
I already have suggested to switch to Ubuntu for the internet PC's, but they are not convinced, because, and they are a bit correct, a lot of people follow a course in for example Word, or Excel, or an introduction organised by certain organisations which are windows based, and those beginners really do freak out as soon as they don't see the windows logo or when an icon is not in the same place as where they are used to find it. Those people do come to exercise on the PC's in the library. That being said, even Open Office is out of the question.

2. Cultural Centre
We use a system, called Recreatex. It is actually built for sport centres, but they've changed it a bit to adapt to cultural centres too. It is used for booking the different locations in the building (theatre, bar, etc...), lending of material (publicity panels, microphones, speakers, ...) and of course the reservations of activities (concerts, theatre, ...).
On top of that, it is web based too. The data is stored in a database of the company, which can be an advantage, for example to access data on a different location. It has a full list of all the people that ever bought a ticket, which is useful for promoting our activities.

My question is, is there an open source alternative for it? I know php and mysql, and I could write something like that myself, but why would I reinvent the wheel if there already is an app out there.

I have googled for it, but these applications are so specific, and not for general use, that it is really hard to find something useful. If there is someone that can help me out. Please do reply.

Grtz,

Bart

---

### Post by Bartje on 2010-12-14
nothing? bump...

---

### Post by Megaptera on 2010-12-14
Have you looked at 'Meeting Room Booking System' number 6 here: [http://blogs.techrepublic.com.com/10things/?p=423](http://blogs.techrepublic.com.com/10things/?p=423)

This quote "MRBS is a system for multi-site booking of meeting rooms. Rooms are grouped by building/area and shown in a side-by-side view. Although the goal was initially to book rooms, MRBS can also be used to book any resource; computers, planes, whatever you want."
From here: [http://sourceforge.net/projects/mrbs/](http://sourceforge.net/projects/mrbs/)

---

### Post by Bartje on 2010-12-14
Looks good, but it is just a little too limited. Ticketing is not included, reservation per seat is quite necessary. It might be useful as an app to start with, and adding functionality with modules. I've looked into the code, but it's not really easy to add code to... Unless I've glanced over the code too quickly, it is not OOP, and does not use MVC for making extra functionality easier to code. Thanks for the suggestion though.

---

### Post by Megaptera on 2010-12-14
Sorry 'bout that.
What about other villages/towns in your area - do they all use Windows or could they have already gone down the linux route?

---

### Post by Bartje on 2010-12-14
It's all windows as far as I have seen. Even when it's about servers it's all windows based. Too bad indeed. I mean, tax payers pay for the licenses too. This leads to ridiculous situations, which I'm not going to explain in depth. I can only say, it is really dirty, and I want to get rid of the situation, or at least offer alternatives, so that they can take their responsibility.

I've started a little by getting an old laptop functioning again, using the linux distribution 'peppermint'. The laptop was even too light for Lubuntu, but peppermint got it alive again, and so far they are impressed. Let's hope this first step will lead to more...

---

### Post by Megaptera on 2010-12-15
Maybe the city of Schoten could offer some ideas? "The Belgian government should start an open source resource centre to help its public administrations increase their use of this type of software, says Jan Verlinden, IT administrator in the city of Schoten.

The city uses a lot of open source applications in the back-end as well as on the desktop and Verlinden says he is often asked to help other cities and municipalities. To him this proves the need for an national open source resource centre." from [http://www.osor.eu/news/be-belgium-needs-an-open-source-resource-centre/?searchterm=None](http://www.osor.eu/news/be-belgium-needs-an-open-source-resource-centre/?searchterm=None)
Also:"The city of Schoten has 33,000 inhabitants and the city administration employs four hundred people. The three IT workers maintain two hundred desktops and twenty servers in fifteen separate offices. The department is using Zarafa, an open source mail and collaboration server identical in functionality to Microsoft Exchange. In the back-end, the IT department is using more than twenty open source applications. It uses for example mail server Postfix, anti-virus application Clamav, content management system Joomla and employs  Asterisk to offer voice over IP telephone services. The city has servers running either the Suse, Centos or Ubuntu GNU/Linux servers distributions. The department uses the open source OTRS to manage requests for computer assistance and troubleshooting.

On the desktops, the city workers find web browser Firefox, PDFcreater, file compression tool Filzip and project management tool Workbench. On a number of PCs OpenOffice is installed.

According to Verlinden, the city is planning to increase its use of open source. "Migrating to such tools is a smooth process. It is very easy to solve problems, and these applications have proven to be very stable and more secure. Our use of is open source is purely pragmatic, it is not out of ideology."

---

