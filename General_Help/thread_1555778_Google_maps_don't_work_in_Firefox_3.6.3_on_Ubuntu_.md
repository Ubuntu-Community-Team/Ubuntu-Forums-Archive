---
title: "Google maps don't work in Firefox 3.6.3 on Ubuntu 10.04"
date: 2010-08-18
forum: General Help
---

### Post by dado2000 on 2010-08-18
Hi guys,

I am having troubles with google maps running on ubuntu. I tried different browsers like Chromium (Chrome) and SeaMonkey but they can't load google maps also. 

When I choose to view some City, a grey box appears and nothing else hapens. This is what its look like when I try to view Mostar:

Thanks for your help in advance.

---

### Post by sanderd17 on 2010-08-18
Is it still not working? I think it is/was a server problem. Google maps uses normal javascript, so that can't be the problem. If e.g. gmail or other javascript sites work, google maps should work to.

---

### Post by dado2000 on 2010-08-18
No, still doesn't work. I figure out three days ago, that Firefox in Ubuntu use some Open Source JavaScript plugin called **OpenJDK** for viewing Java content on web pages. So I found some tutorials how to install Sun Java plugin called **sun-java6-plugin, **now everything is working just fine, except Google maps :(

However I didn't know about those server problems, I'am located in Bosnia and Herzegovina. Maybe this service is still unavalible to our country?????

---

### Post by WBTMagnum on 2010-08-19
I also noticed this problem a few days ago and hereby confirm it for an Ubunty 10.04 machine with Firefox and Opera. 

Seems like the maps.gstatic.com server returns the wrong contents for main.js: 
  [http://maps.gstatic.com/intl/de_ALL/mapfiles/api-3/2/1/main.js](http://maps.gstatic.com/intl/de_ALL/mapfiles/api-3/2/1/main.js) 

It just contains the following code instead of the Javascript: 
```
<frameset rows="100%,*" frameborder="no" border="0" framespacing="0">
	<frame src="http://maps.gstatic.com/?fp=Cy0tfSV2zPDOhPceXEO4ek23uhiZgkXtFD0C5pf3cnPOHV4sP4zOgYkN20c7T8ofkX3UNACv%2Bp2sgx3MYCJD6g%3D%3D&prvtof=hsVVPjcKriQK%2B5YJnS0ElP1IaHr6pjqCDJsaT4AbKNpGXbD9TEKpfzj6UQ3Wlknsx4rOcHQMO%2B0bMkS4ISE62A%3D%3D&poru=asbL2ruerD14Nm%2BHZuqPSMkiVcZG%2FOZU4oPREe1B4onsO93QazH4JXFPKEQGAS%2FtY4csWWZvm51ygP%2BNUd2O8MYJPlLSYi9EnyPMHuljpVA%3D&">
</frameset>
<noframes>
	<body bgcolor="#ffffff" text="#000000">
	<a href="http://maps.gstatic.com/?fp=Cy0tfSV2zPDOhPceXEO4ek23uhiZgkXtFD0C5pf3cnPOHV4sP4zOgYkN20c7T8ofkX3UNACv%2Bp2sgx3MYCJD6g%3D%3D&prvtof=GVOdMWyFThvXM5UG0q7isdFsZsCKrNuuBmDZIkThlDfSRNyaRsfJMub9ikq%2F9F0faILO4dYPmwR59InmzchnlA%3D%3D&poru=QfT%2BW245Bi8B%2BoDb8IRF5m30HM%2FFe06OB7xn5oDPEUOoGdoUFue5rod5pjar5naoX4fr0T%2FnQkpvVOF5VbZqpVwrnnPCzz68eBy28b%2FGmEo%3D&">Click here to proceed</a>.
	</body>
</noframes>
```

Other systems are not effected. I did a quick test under: 
 * openSuse 10.2 
 * Debian 5.0.4 
 * Windows XP 
 * Windows Vista 

The server always returned the JavaScript. 


Very strange that is ... I think I'm going to report this problem to the Google Maps people. 


Best regards, 
Sascha

Update: Posted the problem in the google maps support forum [http://www.google.com/support/forum/p/maps/thread?tid=4fedaf3282e30645&hl=de](http://www.google.com/support/forum/p/maps/thread?tid=4fedaf3282e30645&hl=de)

---

### Post by dado2000 on 2010-08-19
> **WBTMagnum said:**
> 


Very strange that is ... I think I'm going to report this problem to the Google Maps people. 




Do it please, let us know what they said to you. 

I think they are working on this problem, when I tried to view google maps today, I got some results, but still it loads the page very slow and when I choose to view images from satellite nothing hapens, zoom doesn't work also.

---

### Post by dado2000 on 2010-08-20
It works now, server problems.:lolflag:

---

### Post by WBTMagnum on 2010-08-27
> It works now, server problems.

Nice for you. Unfortunately it's still not working for me :-(. 


Best regards, 
Sascha

---

