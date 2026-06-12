---
title: "Need help finding a repository"
date: 2011-08-04
forum: General Help
---

### Post by dogeatery on 2011-08-04
I'm a recovering Peppermint OS user who recently upgraded to Peppermint 2 and was disappointed by the release.  I switched to Easy Peasy on my netbook, instead, and so far I really like it.  Still, I DID like Peppermint's integration of Chrome for stand-alone apps.  They called it Ice. 

Can anyone point me to the main Peppermint OS repositories so I can add them and download Ice?

---

### Post by xdominex on 2011-08-04
Is this what you are looking for?

[https://launchpad.net/~kendalltweaver/+archive/peppermint?field.series_filter=]("https://launchpad.net/%7Ekendalltweaver/+archive/peppermint?field.series_filter=")

Note that only Lucid and Natty are currently supported, so you will have to change the file names and contents of the files in /etc/apt/sources.list.d if you are using a distribution other than Natty or Lucid. That's easy, though. Just find any instances of "Maverick" or whatever and replace them with "Natty" (or "Lucid", if you prefer).

Hope this helped!

With regards,
XDomineX

---

### Post by dogeatery on 2011-08-05
Yeah that's exactly what I'm looking for!  Thanks a ton!

> you will have to change the file names and contents of the files in  /etc/apt/sources.list.d if you are using a distribution other than Natty  or Lucid. That's easy, though. Just find any instances of "Maverick" or  whatever and replace them with "Natty"

Are you sure you don't have this backward?  Should I change Natty/Lucid to "Maverick"?  (I assume you said Maverick because that is what Easy Peasy is based on?)

---

### Post by xdominex on 2011-08-05
I am quite sure. "add-apt-repository" automatically adds the version of the repository that matches your distro. If your distro is Maverick, it will automatically add the Maverick version... but there IS no Maverick version of this PPA, so apt-get will try (and fail) to retrieve packages from a non-existent "Maverick" version of the PPA for installation. If you change the apt configuration files to reflect a Natty or Lucid PPA (Natty is probably best for you), apt-get will retrieve packages from the Natty or Lucid version of the PPA according to which distro you configured your apt configuration files to reflect. The reason I know all of this is that I have a list of PPAs I always add when I reinstall Ubuntu, but when Natty was still in development, many of the PPAs did not have a Natty version. This meant that, to use packages from those PPAs in the Natty betas, I had to manually change "natty" to "maverick" in both the names and contents of any apt configuration files for PPAs that had a Maverick version but no Natty version.

---

### Post by dogeatery on 2011-08-06
Thanks for the help!  Turns out that your extra instructions were a moot point.  I ran an update and Easy Peasy appears to be running Lucid now (at least, all my repositories listed Lucid)

---

### Post by xdominex on 2011-08-06
Well, I figured the extra instructions would probably be unnecessary but wanted to have them there for you just in case ;). I'm glad things worked out for you!

With regards,
XDomineX

---

