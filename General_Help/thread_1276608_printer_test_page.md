---
title: "printer test page"
date: 2009-09-27
forum: General Help
---

### Post by cornflake000 on 2009-09-27
Greetings...

Is there a way to change the print test page?  I don't like to use up my ink cartridges printing an Ubuntu masterpiece whenever I simply need to check the basics on network printers.

thanks

---

### Post by StuartN on 2009-09-27
> **cornflake000 said:**
> Is there a way to change the print test page?

Make your own minimum-ink message in <whatever package> and print it to test the printer. Prining the printer test page doesn't give any more information, other than checking the colour and grey levels on the output.

---

### Post by cornflake000 on 2009-09-27
Thanks for the reply...

That works fine if you're on a single machine but when testing a bunch of networked computers, it would be nice to have the "print test page" option on the printer properties window rather than having another program which could have it's own problems in between. Having a direct from "system" test page helps to focus on the driver, eliminating other unknowns.

---

### Post by philinux on 2009-09-27
> **cornflake000 said:**
> Greetings...

Is there a way to change the print test page?  I don't like to use up my ink cartridges printing an Ubuntu masterpiece whenever I simply need to check the basics on network printers.

thanks

+100%

I've even raised a bug.
[https://bugs.launchpad.net/ubuntu/+source/system-config-printer/+bug/298935](https://bugs.launchpad.net/ubuntu/+source/system-config-printer/+bug/298935)
I think the best thing is to use cups and get the printer to perform it's own self test.
Or mtink >check nozzles.

---

### Post by StuartN on 2009-09-27
You can always replace /usr/share/system-config-printer/testpage-a4.ps (or testpage-letter.ps) with your own print job.

It looks like nobody has implemented a dialogue to select the custom_testpage parameter.

---

### Post by cornflake000 on 2009-09-27
Well...

I just renamed the test pages in /usr/share/system-config-printer and now the CUPS version prints instead which is much more appropriate I would say.  

So I guess that's that.

Thanks!

---

