---
title: "Print Quality canon MP ubuntu 12.04"
date: 2012-05-02
forum: General Help
---

### Post by isaacjun16 on 2012-05-02
Hi, ):P

So far I'm happy with the upgrade I did on my computer to 12.04. The only "problem" I have now is with my printer. I have a Canon MP210, in ubuntu 10.04 I was using the printer with the driver from the canon website, and I was able to change the quality print by adding to the ppd file:

```

*OpenUI *CNQuality/Quality: PickOne
*DefaultCNQuality: 3
*CNQuality 2/High: "2"
*CNQuality 3/Normal: "3"
*CNQuality 4/Standard: "4"
*CNQuality 5/Economy: "5"
*CloseUI: *CNQualityE
```

but now I see that ubuntu 12.04 comes with the drivers from Guteprint wich is grate, but, I was chequing the ppd file for my printer and I notice that the print quality comes included by default on the file, but It doesn't give me to much options.

```
*ColorKeyWords: "Quality"
*OpenUI *StpQuality/Print Quality: PickOne
*OPOptionHints Quality: "dropdown"
*OrderDependency: 10 AnySetup *StpQuality
*StpStpQuality: 0 1 0 0 255 0.000 0.000 0.000
*DefaultStpQuality: None
*StpDefaultStpQuality: Standard
*StpQuality None/Manual Control:	"<</HWResolution[600 600]/cupsRowFeed 1>>setpagedevice"
*StpQuality Standard/Standard:	"<</HWResolution[600 600]/cupsRowFeed 2>>setpagedevice"
*CloseUI: *StpQuality
```

I'm not sure what can I do to be able to change the quality, and adding the option I mention before doesn't work, I will really apreciate any help I can get, thank for your time.

---

### Post by marrok1 on 2012-05-02
You might just want to use the ppd file you were using before instead of the gutenprint ones. You can add a ppd file by going to the cups web interface at: [http://localhost:631](http://localhost:631)

---

### Post by isaacjun16 on 2012-05-08
Hi, sorry I took so long to repply it, (to much school :guitar:).

I tried what you sugested but the ppd file (the one I was using before) is does not work with the drivers that already come with ubuntu, also there si another thing with the ppd file of guteprint, when I change to grayscale and then try to go back to color it gets "stuck" and doesnt change back, so what I did was to remove the printer and add it again, I dont know what to do I don't want to go back to 10.04, I hopping I can do something about it.

PS: the problem I get with the old ppd files is that looks for a files witch is not available: pstocanonij.

---

