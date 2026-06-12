---
title: "ibm-acpi not working!"
date: 2006-02-22
forum: General Help
---

### Post by bigblop on 2006-02-22
I have added: "ibm_acpi" to /etc/modules. I have then restarted the computer but it only works for the first 5 minutes, then the fan goes on again permanently eventhough I have only emacs running. Any ideas on how I get the acpi module to work for more than 5 minutes?

---

### Post by JELaVallee on 2006-02-22
[QUOTE=bigblop]I have added: "ibm-acpi" to /etc/modules. I have then restarted the computer but it only works for the first 5 minutes, then the fan goes on again permanently eventhough I have only emacs running. Any ideas on how I get the acpi module to work for more than 5 minutes?[/QUOTE]

bigblop,

Did you see my response here: [http://www.ubuntuforums.org/showthread.php?t=134290](http://www.ubuntuforums.org/showthread.php?t=134290)

do and lsmod|grep acpi and see if it's actually being loaded first...

cheers,
Etienne

---

### Post by bigblop on 2006-02-22
I have read your reply and have changed it to ibm_acpi. When I do lsmod | grep ibm_acpi it returns with:

ibm_acpi    17908    0

So the module is running. Guess it does not work with my T40/p model. Maybe it has something to do with it being a P model.

---

### Post by JELaVallee on 2006-02-22
[QUOTE=bigblop]I have read your reply and have changed it to ibm_acpi. When I do lsmod | grep ibm_acpi it returns with:

ibm_acpi    17908    0

So the module is running. Guess it does not work with my T40/p model. Maybe it has something to do with it being a P model.[/QUOTE]

I have a T43p and it's been working fine... My fan does run pretty pretty much continuously, but it's at what sounds like the second lowest speed and really isn't all that annoying/problematic.  When I run in WindowsXP on this machine it's usually running the fan too.

Does hibernate, sleep and unplugging the power cord work without a hitch for you?  If so, then acpi is working and you may just require modifications to your processor/thermal/fan configurations in /proc/acpi, but I'm not positive what these should be.

I'll dig around some more too... it's something I'm interested in having properly/easily tuned on my machine as well.

cheers,
Etienne

---

### Post by JELaVallee on 2006-02-23
[QUOTE=bigblop]I have read your reply and have changed it to ibm_acpi. When I do lsmod | grep ibm_acpi it returns with:

ibm_acpi    17908    0

So the module is running. Guess it does not work with my T40/p model. Maybe it has something to do with it being a P model.[/QUOTE]

bigblop,

Just dug out this how-to on the ThinkWiki site:
[http://www.thinkwiki.org/wiki/How_to_control_fan_speed](http://www.thinkwiki.org/wiki/How_to_control_fan_speed)

Includes a script management solution that should work fine with ibm_acpi when passed the experimental=1 flag.

I'm going to give it a shot on my T43p, but the T40 is listed as working iwth the script as well.  Will let you know how it goes.

cheers,
Etienne

---

