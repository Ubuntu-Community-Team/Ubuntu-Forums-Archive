---
title: "Windows Address Book"
date: 2009-07-04
forum: General Help
---

### Post by 6205 on 2009-07-04
I'm trying to import into Evolution Mail Windows address book *.wab file but so far without a success. Are there really no working solutions for this? I have Googled everywhere but it seem that it is not possible :/ 

I have only linux system so i cannot boot into Windows and export it in other formats like csv. Also linux Thunderbird cannot import Outlook Express address book (but Win-version can..)

'libwab' looks interesting, but it's old and not available for Ubuntu :( 
[http://lilith.tec-man.com/libwab/](http://lilith.tec-man.com/libwab/)

Any suggestions ?  Thanks..

---

### Post by bertmanphx on 2009-07-04
Hello,
Evolution has an import feature listed under File - Import.....
Point the utility directly at it.  If that does not work, then export the address book from within your Windows machine to a .csv, or ldap file type.  These I know, Evolution will import easily.

Regards,

bertmanphx

---

### Post by michy99 on 2009-07-04
If you want to compile libwab, I will be happy to walk you through it. Not too complicated, really.

---

### Post by sdaau on 2011-07-12
> **michy99 said:**
> If you want to compile libwab, I will be happy to walk you through it. Not too complicated, really.

Just found this walkthrough: [» Convert Windows Address Book To LDIF schlasim's ubuntu blog](http://blogs.ethz.ch/ubuntu/2010/01/02/wab-to-ldif/) -  just use the tar.gz link from the [www.filewut.com:libwab](http://www.filewut.com/spages/page.php/software/libwab) homepage instead..

Cheers!

---

