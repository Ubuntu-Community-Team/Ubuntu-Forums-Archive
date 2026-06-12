---
title: "Did some TRIM testing for anyone interested (AHCI/RAID/IDE tested)"
date: 2011-11-23
forum: General Help
---

### Post by Krause on 2011-11-23
Ive been curious for a while to see what controllers/modes TRIM would actually work on in Linux and finally got around to doing some tests to verify it. With Linux your actually able to write and read specific sector ranges on the hard drive so its pretty easy to verify.(guide here if your interested [http://sites.google.com/site/lightrush/random-1/checkiftrimonext4isenabledandworking](http://sites.google.com/site/lightrush/random-1/checkiftrimonext4isenabledandworking))

One of the main questions I had was if TRIM was supported on Intel controllers in Raid mode given they weren't part of an Array. And I haven't been able to find any information out there on it.

On this motherboard I have an ICH10R Controller and a JMicron Controller, ive tested on both and in all available modes (AHCI/RAID/IDE)

**ICH10R:**

AHCI: As expected, TRIM worked flawless, right after the file was deleted, the sectors it occupied were all zeros.

RAID (Not part of an array): This surprised me, TRIM actually worked. It was a fairly recent Intel driver (Well a little over a year, maybe not that recent) that allowed this to work on Windows and I wasn't expecting it to be functional in Linux yet. I tested with with 2 drives connected so that it didn't just default back to AHCI mode, but I did not actually create a RAID array along side the SSD. I don't think that would make a difference but it might be worth noting.
It will be interesting to see how soon TRIM on a SSD Raid 0 array comes now that Intel has just officially announced it for its upcomming 11 series RST Windows drivers.

IDE: Also a bit of a surprise, TRIM worked fine.


**JMicron:**

I Tested it in AHCI/IDE and neither seemed to pass the TRIM command to the drive. I Was expecting this to work since the Windows default AHCI driver (But not the one provided from JMicron) supposedly works with it. Then again it is incredibly hard to verify on windows without the ability to write and read to specific sectors, so the information could be false.


Overall surprising results to me, It worked in situations I would have assumed it wouldn't, and failed in situations I figured it would (JMicron).

Hopefully this may may be of some use to people!

-Krause

---

