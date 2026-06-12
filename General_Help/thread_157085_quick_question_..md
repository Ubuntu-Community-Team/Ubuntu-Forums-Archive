---
title: "quick question ."
date: 2006-04-08
forum: General Help
---

### Post by newpants2003 on 2006-04-08
can some one tell me the defaul setting for /etc/environment  ?
(installed in english US)
i changed it and other somethings in locale, want to change back to defaul.

the fcixt is not working after i done the change, just wanna back to normal.

---

### Post by llamakc on 2006-04-08
I dunno what language/locale you set up at install but my US English one reads:

```

LANGUAGE="en"

LANG=en_US.UTF-8

```

And you can reconfigure your locale with `sudo dpkg-reconfigure locales` from a Terminal.

---

### Post by newpants2003 on 2006-04-08
i installed in english US 
but now my  /etc/environment  is :
 LANGUAGE="zh_CN:zh:en_US:en"
 LC_CTYPE=zh_CN.UTF-8
 GST_ID3_TAG_ENCODING=GBK
 LC_ALL=zh_CN.utf-8 

 LANG=zh_CN.GBK

locale shows :

  LANG=en_US.UTF-8
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=en_US.UTF-8

and changed gtkrc.zh_CN.utf-8 (i dont know whats that for.) to:

 style "gtk-default-zh-cn" {
       fontset = "-adobe-helvetica-medium-r-normal--12-*-*-*-*-*-iso8859-1,\
                  -*-*-medium-r-normal--16-*-*-*-*-*-gb2312.1980-0,*-r-*"
}
class "GtkWidget" style "gtk-default-zh-cn" 

is some thing wrong here?

---

