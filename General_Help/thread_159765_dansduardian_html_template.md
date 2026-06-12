---
title: "dansduardian html template"
date: 2006-04-13
forum: General Help
---

### Post by freemanda3 on 2006-04-13
Sometimes i feel like taking my server and throwing it out the window. at this point i am really frustrated with dansguardian and the report level of 3. if you follow the config file it clearly states if you want to use the html template then use this level. i have googled all day long and read other dansguardian.conf files, but after setting up my own customized html file i can not get it to display. it does eveything but display my html file. ](*,) 
any help would be appreciated

---

### Post by AnthonyLewis on 2006-04-13
Did you check the other settings in the config file and make sure that your template is in the right place?

Here's part of my config file for example:

```

reportinglevel = 3
languagedir = '/etc/dansguardian/languages'
language = 'ukenglish'

```

So, my html template is at /etc/dansguardian/languages/ukenglish/template.html

Hope this helps,

Anthony Lewis

---

### Post by freemanda3 on 2006-04-13
thanx a lot Anthony,

in my config file i have exactly the same locationfor the ukenglish directory but it still doesn't work .As a matter of fact here it is 

```
# DansGuardian config file for version 2.8.0

# **NOTE** as of version 2.7.5 most of the list files are now in dansguardianf1.conf


# Comment this line out once you have modified this file to suit your needs
#UNCONFIGURED


# Web Access Denied Reporting (does not affect logging)
#
# -1 = log, but do not block - Stealth mode
#  0 = just say 'Access Denied'
#  1 = report why but not what denied phrase
#  2 = report fully
#  3 = use HTML template file (accessdeniedaddress ignored) - recommended
#
reportinglevel = 3

# Language dir where languages are stored for internationalisation.
# The HTML template within this dir is only used when reportinglevel
# is set to 3. When used, DansGuardian will display the HTML file instead of
# using the perl cgi script.  This option is faster, cleaner
# and easier to customise the access denied page.
# The language file is used no matter what setting however.
#
languagedir = '/etc/dansguardian/languages'
htmltemplate = '/etc/dansguardian/languages/ukenglish/access.html'

# language to use from languagedir.
language = 'ukenglish'

# Logging Settings
#


```

i see one thing and that my template iss named access.html ...
i don't believe that should make a difference since it is a basic html file. i had to go to the beach and get away because it was bothering me so bad :mad:

---

### Post by freemanda3 on 2006-04-14
its a new day and i still have the same problem. if there is anyone with experience with this content filter then let me know if you have any suggestions

---

### Post by freemanda3 on 2006-04-14
sorry for the inconvience guys but i have finally figured this thing out. the template file has to be named template.html. even though in the conf file i specified the path, when i renamed the access.html to template.html it all worked. i guess when you slow down and take your time you can figure this thing out. its just that when you are working on the commanfd line things can get crazy sometimes 

 lata:-D

---

