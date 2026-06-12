---
title: "Error Message in Synaptic Package manager"
date: 2009-08-19
forum: General Help
---

### Post by heinzbitte on 2009-08-19
I got my printer working by using the instructions in [http://ubuntuforums.org/showpost.php?p=2786642&postcount=7](http://ubuntuforums.org/showpost.php?p=2786642&postcount=7) this post.  

It worked very well, except for one part of it.  

"The scipt installs everything but falls over at the last hurdle with an error message saying it hasn't worked........but it has !"

Now, whenever I use add/remove I get that error message after installing something.

Is there a way to get rid of the error message, without removing the printer driver? 

Thanks

---

### Post by heinzbitte on 2009-08-19
E: magicolor2530dl: subprocess post-installation script returned error exit status 2

Here is the error message that comes up in a new window.

---

### Post by philinux on 2009-08-19
You'll have to edit the file, looks like a bugette.
```
gksu gedit /var/lib/dpkg/info/magicolor2530dl.postinst
```

Look at line 10 where it expects a fi and not a (

Have a browse in the info folder there are loads of postinstall files to compare with.

---

### Post by heinzbitte on 2009-08-19
> **philinux said:**
> You'll have to edit the file, looks like a bugette.
```
gksu gedit /var/lib/dpkg/info/magicolor2530dl.postinst
```

Look at line 10 where it expects a fi and not a (

Have a browse in the info folder there are loads of postinstall files to compare with.

So, I should just try to get it to look like the others that don't give me error messages?  And, if I edit it, it won't change the functionality of the printer, will it? 

Thanks

---

### Post by heinzbitte on 2009-08-19
```
#!/bin/sh
RPM_INSTALL_PREFIX=
export RPM_INSTALL_PREFIX
if [ "$1" = "2" ]; then
   PPD_DIR="/etc/cups/ppd/"
   FILETYPE=".ppd"
   LPADMIN="/usr/sbin/lpadmin"
   KM_PPD_DIR="/usr/share/cups/model/KONICA_MINOLTA"
   if [ -x $LPADMIN ] && [ -d $PPD_DIR ] && [ -n "`ls -1A ${PPD_DIR}`" ]; then
      KMPPDS=(`grep -l "magicolor 2530 DL" ${PPD_DIR}*`)
      for kmppd in ${KMPPDS[@]}; do
         ppdFile=${kmppd#${PPD_DIR}}
         Printer=${ppdFile%${FILETYPE}}
         ppdFileNew=`find "${KM_PPD_DIR}" -name "km2530dl.ppd.gz" -print`
         $LPADMIN -p $Printer -P $ppdFileNew
         if [ $? -eq 0 ]; then
            echo Succeed to update $Printer
         else
            echo Fail to update $Printer
         fi
      done
   fi
fi

if echo $MACHTYPE | grep "suse" ; then
   :
else
   if [ "$1" = "1" ]; then
      if [ -x /etc/init.d/cups ] ; then
	 /etc/init.d/cups restart
      fi
   fi
fi
```

Here is what is there now.  I am a bit unsure as to what I need to change.

Thanks

EDIT:

Sorry for posting so much,  I just changed "(`grep -l "magicolor 2530 DL" ${PPD_DIR}*`)" to "fi"  and everything seems to be working fine now.

thanks for all the help.

---

