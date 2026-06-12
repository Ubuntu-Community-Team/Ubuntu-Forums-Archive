---
title: "Ubuntu LAN + Windows/Office Possible?"
date: 2012-10-12
forum: General Help
---

### Post by jayaq32 on 2012-10-12
Hi Everyone,

I am new to Ubuntu and I was curious if anybody could help me with some  questions I have in setting up a LAN that consists mostly of Ubuntu OS  machines and one Windows XP machine w/MS Office.

I would like to use the XP machine as an "application server" for MS Office that the other Ubuntu workstations could access.

Is this possible? If so, what would be the most ideal setup for this?

What I am unsure about is if there is a convenient way for the Ubuntu  machines to remotely connect to the XP machine and use the MS Office  applications (Word, Access, Excel, Publisher, etc.) in a way that's  ideal for a multi-user environment (about 5 people)?

We are transitioning to Ubuntu + Office Libre and just wanted to make  sure that Win XP + MS Office was still *accessible* in case we need it. 

I have a feeling that our staff would access MS Office (mostly  Word/Access/Excel) from their Ubuntu workstations pretty frequently in  the beginning (and all at the same time) but overtime ultimately phase  out their need for it in favor of Office Libre.

Staff does content creation in mostly word. They work in a  shared/collaborative environment. We're talking mostly documents and  forms and not video or other large media. They also do web surfing/email  via Firefox/Chrome.

The XP box would be your run-of-the-mill Dell Vostro Desktop (Core2Duo, GBLan, 2GB Memory). 

I do have access to a Gb switch to handle the traffic. Though would your standard 100Mbps router/switch suffice?

I know connecting to the XP box via remote desktop through Ubuntu would  be the obvious answer. But is there a user-friendly way to setup access  to the MS Office apps using Remote Desktop for complete beginners? Or is  launching Remote Desktop the easiest method? I am  trying to make the  process as simple as possible for staff that may not know how to  use/launch Remote Desktop - a sort-of "one click" access type of setup  as if the MS app they want to use is actually right there on their  desktop.

Any suggestions would be helpful!

Thank you so much :smile:

---

### Post by Mark Phelps on 2012-10-12
That's probably NOT going to work.  Consider the following limitation on the use of MS Office products -- copied directly from an MS Office license:

> Microsoft Office retail (full packaged product) and original equipment manufacturer (OEM) products released in 2007 or later do not permit network use.

Furthermore:

> Microsoft licenses its desktop applications on a per-device basis. Per-device licensing means a customer must obtain a license for each desktop on or from which the product is used or accessed. For example, when a desktop application is accessed remotely across an organization using Windows Server Remote Desktop Services, a separate desktop application license is required for each desktop from which the application is accessed. 

What this says, basically, is that every "client" Ubuntu machine must have an MS Office license, inclusive of every Office app you want to access remotely.

---

