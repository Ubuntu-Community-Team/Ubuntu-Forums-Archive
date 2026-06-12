---
title: "Accessing smartcard reader on Dell"
date: 2006-02-19
forum: General Help
---

### Post by richardh on 2006-02-19
Just got a new Dell 810 with in built smartcard (chipcard) reader.

For business I need to use a company-supplied chip card for online identity checking.

The Dell specs say the card reader is compliant with ISO 7816.

I found the MUSCLE site but I cant find any consistent HowTo. I cant even find out whether the card reader is working.

I tried installing cardtools, which has cardcommander, and cardcommander2. 

I have started both daemons (separately)
/etc/init.d/cardtools start
/etc/init.d/libcardtools2 start

Both yield errors.

cardtester gives the following output
6:2006/02/19 17-44-04:rt(14429):ctcore_public.c:  340: Opened dir "/usr/share/libchipcard/drivers", reading.
6:2006/02/19 17-44-04:rt(14429):ctcore_public.c:  357: Found file "."
6:2006/02/19 17-44-04:rt(14429):ctcore_public.c:  357: Found file ".."
6:2006/02/19 17-44-04:rt(14429):ctcore_public.c:  357: Found file "kobil.dsc"
6:2006/02/19 17-44-04:rt(14429):ctcore_public.c:  396: Adding drivers from file "/usr/share/libchipcard/drivers/kobil.dsc"
6:2006/02/19 17-44-04:rt(14429):ctcore_public.c:  357: Found file "README"
6:2006/02/19 17-44-04:rt(14429):ctcore_public.c:  357: Found file "ctapi-fake.dsc"
6:2006/02/19 17-44-04:rt(14429):ctcore_public.c:  396: Adding drivers from file "/usr/share/libchipcard/drivers/ctapi-fake.dsc"
6:2006/02/19 17-44-04:rt(14429):ctcore_public.c:  357: Found file "towitoko.dsc"
6:2006/02/19 17-44-04:rt(14429):ctcore_public.c:  396: Adding drivers from file "/usr/share/libchipcard/drivers/towitoko.dsc"
6:2006/02/19 17-44-04:rt(14429):ctcore_public.c:  357: Found file "cyberjack.dsc"
6:2006/02/19 17-44-04:rt(14429):ctcore_public.c:  396: Adding drivers from file "/usr/share/libchipcard/drivers/cyberjack.dsc"
6:2006/02/19 17-44-04:rt(14429):ctcore_public.c:  357: Found file "orga.dsc"
6:2006/02/19 17-44-04:rt(14429):ctcore_public.c:  396: Adding drivers from file "/usr/share/libchipcard/drivers/orga.dsc"
Initializing core
5:2006/02/19 17-44-04:rt(14429):ctcore.c: 1141: Checking for PC/SC readers
3:2006/02/19 17-44-04:rt(14429):ctdriver_pcsc.c:  785: SCard error: 8010001d
4:2006/02/19 17-44-04:rt(14429):ctcore.c:  621:  Severity: Error Type: CTCore Code: Driver IO error (2)
4:2006/02/19 17-44-04:rt(14429):ctcore.c: 1149: PCSC supported but not available
3:2006/02/19 17-44-04:rt(14429):readertest.c:  279: No driver given.

I cant seem to work out what the Dell specs mean by ICO 7816 in reference to the card reader, when the literature indicates that 7816 refers to the cards. Also confusing is the PC/SC standard (a MS thing?) and the Open Card Framework.

Any suggestions about what to do next?

I am running hoary hedgehog



Richard

---

