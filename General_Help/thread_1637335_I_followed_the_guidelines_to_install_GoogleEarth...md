---
title: "I followed the guidelines to install GoogleEarth..."
date: 2010-12-04
forum: General Help
---

### Post by rva1945 on 2010-12-04
[(http://ubuntuguide.net/how-to-install-google-earth-6-beta-in-ubuntu-with-some-problem-fixed/comment-page-1#comment-4315)]("http://ubuntuguide.net/how-to-install-google-earth-6-beta-in-ubuntu-with-some-problem-fixed/comment-page-1#comment-4315")


...but


No error messages, I even got the Installation complete, congratulations, etc. 
 But it doesn’t run. Not even from the Applications/Internet/Google  Earth option, neither from terminal, norby double clicking on  /home/robert/googleearth, it doeas nothing. Version 5 worked but now  it’s uninstalled, and version 6 doesn’t run, so no Google Earth. I have  Ubuntu 9.10
 

In /home/robert/google-earth folder there's a googleearth-bin, I am the owner, I granted read and write access to my group, checked Allow executing as a program, but to no avail.




HELP!

---

### Post by krishnandu.sarkar on 2010-12-04
Look at this to troubleshoot : [http://ubuntuguide.org/wiki/Ubuntu:Maverick#Google_Earth](http://ubuntuguide.org/wiki/Ubuntu:Maverick#Google_Earth)

Sorry didn't noticed 9.10 : See this then [http://ubuntuguide.org/wiki/Ubuntu:Karmic#Google_Earth](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Google_Earth)

---

### Post by rva1945 on 2010-12-04
> **krishnandu.sarkar said:**
> Look at this to troubleshoot : [http://ubuntuguide.org/wiki/Ubuntu:Maverick#Google_Earth](http://ubuntuguide.org/wiki/Ubuntu:Maverick#Google_Earth)

Sorry didn't noticed 9.10 : See this then [http://ubuntuguide.org/wiki/Ubuntu:Karmic#Google_Earth](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Google_Earth)


Dobuble clicked on the deb file, then, after being installed:

Installation finished
Package googleearth_6.0.0.1735+0.5.6-1_i386.deb was installed

in the terminal details it says:

Processing triggers for desktop-file-utils...
Processing triggers for shared-mime-info...

unknown media type in type all/allfiles
unknown media type in type uri/mms
unknown media type in type uri/mmst
unknown media type in type uri/mmsu
unknown media type in type uri/pnm
unknown media type in type uri/rtspt
unknown media type in type uri/fonts/package
unknown media type in type uri/interface/x-winamp-skin

Processing triggers for menu...

And Applications/Internet/Google Earth appears, but shouldn't it be 3d Google Earth ...?

AND OF COURSE I CLICK ON IN AND NOTHING HAPPENS.

---

### Post by SeijiSensei on 2010-12-04
> **rva1945 said:**
> AND OF COURSE I CLICK ON IN AND NOTHING HAPPENS.

I found I needed to install the "lsb-core" package to make Google Earth work on my Maverick system.  From reading other commentators on this problem with other Ubuntu versions, this usually fixes it.

---

