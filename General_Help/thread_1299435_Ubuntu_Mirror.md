---
title: "Ubuntu Mirror"
date: 2009-10-23
forum: General Help
---

### Post by rockstarrem on 2009-10-23
Please move this to the correct area if I am not posting in it.

I have unlimited bandwith/space and would like to mirror Ubuntu. I have looked into this in the mirroring pages and can't seem to find straight forward instructions on how to do this. Could someone help me out and talk me through mirroring Ubuntu? 

Thanks!

---

### Post by zzzBrett on 2009-10-23
Have you seen this?

[http://www.ubuntu.com/getubuntu/mirror](http://www.ubuntu.com/getubuntu/mirror)

---

### Post by rockstarrem on 2009-10-23
Hello,

Yes, I have seen that, but it's not really straight forward. I do have a slight head ache right now but it shouldn't affect my thinking that much :P. If someone could point me in the right direction (clearly) I will be happy to make a guide for other people that would like to do mirrors.

---

### Post by zzzBrett on 2009-10-23
Are you asking how to actually host the files, as in an FTP / HTTP file server, or do you mean the process of getting the mirror 'registered', or both, or something totally different?

---

### Post by rockstarrem on 2009-10-23
Well, I'm pretty good with web servers, but basically here's what I want to know:

Do they want me to set up a process for Ubuntu release to automatically get uploaded? If so, how?

What do they mean by 
> 
For archive you need to make the following URLs work:

    [http://iso-country-code.archive.ubuntu.com/ubuntu/](http://iso-country-code.archive.ubuntu.com/ubuntu/)

    and

    [ftp://iso-country-code.archive.ubuntu.com/ubuntu/](ftp://iso-country-code.archive.ubuntu.com/ubuntu/)

?

---

### Post by zzzBrett on 2009-10-23
Take a look at the next page from that:
[http://www.ubuntu.com/getubuntu/mirror/3](http://www.ubuntu.com/getubuntu/mirror/3)

Does the "Two Stage Mirroring" and this link help any?
[https://lists.ubuntu.com/archives/ubuntu-mirrors-announce/2006-August/000002.html](https://lists.ubuntu.com/archives/ubuntu-mirrors-announce/2006-August/000002.html)

---

### Post by rockstarrem on 2009-10-23
I think that helps now actually, but what about the

> 
For archive you need to make the following URLs work:

[http://iso-country-code.archive.ubuntu.com/ubuntu/](http://iso-country-code.archive.ubuntu.com/ubuntu/)

and

[ftp://iso-country-code.archive.ubuntu.com/ubuntu/](ftp://iso-country-code.archive.ubuntu.com/ubuntu/)


part? Let's say I want my mirror to be [http://ubuntu.digitalstance.com/releases/](http://ubuntu.digitalstance.com/releases/) or something, could it work that way? That's what's really confusing me now.

---

### Post by rockstarrem on 2009-10-24
I made an example thing but files are not being downloaded mostly, just directories being created: [http://www.digitalstance.com/ubuntu/releases/](http://www.digitalstance.com/ubuntu/releases/)

I ran the script and adapted it to my environment from this page: [https://lists.ubuntu.com/archives/ubuntu-mirrors-announce/2006-August/000002.html](https://lists.ubuntu.com/archives/ubuntu-mirrors-announce/2006-August/000002.html)

---

### Post by Ravernomina on 2009-10-24
_**Bandwidth requirements**_

Predicting the bandwidth requirement for becoming a Ubuntu mirror can be difficult. There are number of indicators of bandwidth usage which can be used for a guide.

Ubuntu users are encouraged to download from Ubuntu mirrors within their own country, so countries with a large population of Ubuntu users have a high bandwidth requirement for hosting a Ubuntu mirror. Conversely, Ubuntu mirrors located in countries with a small Ubuntu user population such as Indonesia will have a very low bandwidth requirement for hosting a Ubuntu mirror.

A popular Ubuntu mirror located in the United States, which has a high population of Ubuntu users, can expect to use up to 400-500 megabits of bandwidth or more. If your mirror will target a large group it may be important to apply bandwidth restrictions or Quality of Service rules to avoid impacting other systems or services on the network the Ubuntu mirror is hosted on. An Ubuntu mirror located in Indonesia, a country with a smaller Ubuntu population, may see no more than 10 megabits of bandwidth in a peak period.

Because Ubuntu users are encouraged to download from mirrors within their own country, it is important to consider national bandwidth instead of international bandwidth.

If you are unsure of the bandwidth requirements of hosting an Ubuntu mirror within your country, contact the Ubuntu mirror team for assistance.

_**Disk Space Requirements**_

To mirror the Ubuntu archive, you will need 220 gigabytes with room to grow. To mirror the Ubuntu releases you will need about 30 gigabytes. Release disk space is generally constant while archive disk space will continue to grow.



**_Register your mirror_**

We have transferred our Ubuntu mirror pages to a new Launchpad mirror verification and publication system. The aim of this service is to replace the manually maintained download pages with a more detailed and complete automated reporting system. One of the most important features of the new service is that it allows mirror administrators to self publish detailed information about their mirrors and maintain that information using the Launchpad interface.

Please submit the details of your mirror using the following URL:

[https://launchpad.net/ubuntu/+newmirror]("https://launchpad.net/ubuntu/+newmirror")

You will need to register your mirror separately for Ubuntu archives and Ubuntu releases.

If you have not already done so, you will need to to create a Launchpad user account before you can submit your mirror. After your mirror is registered we will manually review and verify the entry to ensure the person or organisation submitting the entry is the owner or administrator of the mirror. Once verified, the mirror will be marked as an official mirror.  Verification of newly submitted mirrors can take up to 48 hours before being published as official mirrors.
If your mirror is not submitted to Launchpad it will not be listed on the download page.

---

### Post by rockstarrem on 2009-10-24
I have the requirements and all that, but why would I register the mirror if they're not even downloading the files? Do I register first?

---

### Post by Ravernomina on 2009-10-24
> **rockstarrem said:**
> I have the requirements and all that, but why would I register the mirror if they're not even downloading the files? Do I register first?
Register your mirror

We have transferred our Ubuntu mirror pages to a new Launchpad mirror verification and publication system. The aim of this service is to replace the manually maintained download pages with a more detailed and complete automated reporting system. One of the most important features of the new service is that it allows mirror administrators to self publish detailed information about their mirrors and maintain that information using the Launchpad interface.

Please submit the details of your mirror using the following URL:

[https://launchpad.net/ubuntu/+newmirror](https://launchpad.net/ubuntu/+newmirror)

You will need to register your mirror separately for Ubuntu archives and Ubuntu releases.

If you have not already done so, you will need to to create a Launchpad user account before you can submit your mirror. After your mirror is registered we will manually review and verify the entry to ensure the person or organisation submitting the entry is the owner or administrator of the mirror. Once verified, the mirror will be marked as an official mirror. Verification of newly submitted mirrors can take up to 48 hours before being published as official mirrors.
If your mirror is not submitted to Launchpad it will not be listed on the download page.






***_[COLOR="Red"]YOU REGISTER, YOU GET THE FILES, YOU BECOME A MIRROR[/COLOR]_***

---

### Post by rockstarrem on 2009-10-24
Alrighty, again, so I need to register first? I understand your trying to help but all you are doing is copying and pasting information I said was confusing to me.

---

### Post by Ravernomina on 2009-10-24
> **rockstarrem said:**
> Alrighty, again, so I need to register first? I understand your trying to help but all you are doing is copying and pasting information I said was confusing to me.
Register your mirror

We have transferred our Ubuntu mirror pages to a new Launchpad mirror verification and publication system. The aim of this service is to replace the manually maintained download pages with a more detailed and complete automated reporting system. One of the most important features of the new service is that it allows mirror administrators to self publish detailed information about their mirrors and maintain that information using the Launchpad interface.

Please submit the details of your mirror using the following URL:

[https://launchpad.net/ubuntu/+newmirror](https://launchpad.net/ubuntu/+newmirror)

You will need to register your mirror separately for Ubuntu archives and Ubuntu releases.

If you have not already done so, you will need to to create a Launchpad user account before you can submit your mirror. A***_[COLOR="Red"]fter your mirror is registered we will manually review and verify the entry to ensure the person or organisation submitting the entry is the owner or administrator of the mirror. Once verified, the mirror will be marked as an official mirror. Verification of newly submitted mirrors can take up to 48 hours before being published as official mirrors.[/COLOR]_***
If your mirror is not submitted to Launchpad it will not be listed on the download page.


so yes that means once you register you get the files and become a ubuntu mirror

---

### Post by rockstarrem on 2009-10-24
Thanks,

I do feel like an idiot, but next time just be straight forward :).

---

### Post by zzzBrett on 2009-10-24
> **rockstarrem said:**
> Thanks,

I do feel like an idiot, but next time **[COLOR="Red"]just be straight forward[/COLOR]** :).

x2.  No need to be rude.

---

