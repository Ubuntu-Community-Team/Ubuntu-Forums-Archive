---
title: "How/why does line in /etc/rc.local introduce security hole?  Can I fix it?"
date: 2010-04-03
forum: General Help
---

### Post by SnickerSnack on 2010-04-03
I used the following method to turn off the bluetooth hardware in my laptop:

[http://www.thinkwiki.org/wiki/Installing_Ubuntu_9.04_(Jaunty_Jackalope)_on_an_X61_Tablet#Useful_Task:_Disable_Bluetooth_on_Startup](http://www.thinkwiki.org/wiki/Installing_Ubuntu_9.04_(Jaunty_Jackalope)_on_an_X61_Tablet#Useful_Task:_Disable_Bluetooth_on_Startup)

The instructions say that changing permissions on /proc/acpi/ibm/bluetooth  can cause a vulnerability, so can I remove the vulnerability by simply adding

chmod 666 /proc/acpi/ibm/bluetooth 
echo "disable" > /proc/acpi/ibm/bluetooth
chmod 644 /proc/acpi/ibm/bluetooth 

to the /etc/rc.local instead of

chmod 666 /proc/acpi/ibm/bluetooth 
echo "disable" > /proc/acpi/ibm/bluetooth

?  Does changing the permissions back close the security hole, or am I missing the reason there's a security risk?

Thanks.

---

### Post by prodigy_ on 2010-04-03
It's explained there actually: **chmod 666** equals to **-rw-rw-rw-** permissions. Means everyone has write access to a file.

---

### Post by SnickerSnack on 2010-04-03
> **prodigy_ said:**
> It's explained there actually: **chmod 666** equals to **-rw-rw-rw-** permissions. Means everyone has write access to a file.

Yes, but then shouldn't it be easy to fix by immediately changing the permissions back?  That's what led me to believe there was something more to it.  I'll have to see if bluetooth is still turned off if the permissions are changed back.

If the fix is so simple, why isn't it in the how-to itself?  (rhetorical q)

---

### Post by prodigy_ on 2010-04-03
> **SnickerSnack said:**
> Yes, but then shouldn't it be easy to fix by immediately changing the permissions back?
In this case you don't need to change permissions at all. AFAIK, **rc.local** should be executed with root privileges at startup.

---

### Post by SnickerSnack on 2010-04-03
> **prodigy_ said:**
> In this case you don't need to change permissions at all. AFAIK, **rc.local** should be executed with root privileges at startup.

That's what I suspected, but, of course I assumed there had to be a reason it was needed if the how-to said it was needed but also said it might be a security risk.

I tried it with a line changing permissions back, and it works fine.  I'll just remove the chmod lines.  Thanks for you help.

I'll also see about getting the how-to fixed.

---

