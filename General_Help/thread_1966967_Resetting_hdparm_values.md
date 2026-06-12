---
title: "Resetting hdparm values"
date: 2012-04-27
forum: General Help
---

### Post by Mahkoe on 2012-04-27
Awhile back I found a great article on maximizing battery life. One of the commands was "sudo hdparm -B 1 -S 12 /dev/sda", which sets it to aggressive power savings mode and spins it down after 60 seconds. I used it, and got out an entire extra hour from my battery. After I plugged my laptop back in, I no longer needed these settings, so I looked through the hdparm manpage to see if there was any kind of "reset to defaults" sort of deal. (I should have done that first, but there's no point fretting about it now). I did in fact find what I was looking for, but with a tiny little drawback:

--dco-restore
Reset all drive settings, features, and accessible capacities back to factory defaults and full capabilities. This command will fail if DCO is frozen/locked, or if a -Np maximum size restriction has also been set. This is EXTREMELY DANGEROUS and will very likely cause massive loss of data. DO NOT USE THIS COMMAND.

To be quite honest, I doubt whether it has anything to do with the values I set, anyway. So, getting to the point: Will the --dco-restore work if the DCO isn't locked and there are no -Np maximum size restrictions? Will rebooting my system set it back to the way it was? And if none of those work, does anyone know how to put things right?

Thanks

---

### Post by dcstar on 2012-04-28
> **Mahkoe said:**
> Awhile back I found a great article on maximizing battery life. One of the commands was "sudo hdparm -B 1 -S 12 /dev/sda", which sets it to aggressive power savings mode and spins it down after 60 seconds. I used it, and got out an entire extra hour from my battery. After I plugged my laptop back in, I no longer needed these settings, so I looked through the hdparm manpage to see if there was any kind of "reset to defaults" sort of deal.
.........

You do not "reset" the whole drive just to change some minor settings, just change those individual settings.

---

