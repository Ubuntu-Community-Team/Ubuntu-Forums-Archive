---
title: "Redsail 1360c Vinyl Plotter"
date: 2011-11-20
forum: General Help
---

### Post by Jonny87 on 2011-11-20
I have a Redsail 1360c Vinyl Plotter that I would like to get working in Linux. I can get it working MS windows if needed but would rather it in Linux. I have tried Tux Plot but that didn't seem to work. Ideally I want something that will easily plot the designs from some sort up to date application such as (or similar to) Inkscape.

Would rather stick to free software i possible but would consider paying a small fee if I know for sure that it will work.

---

### Post by hansdown on 2011-11-20
Hi, Jonny87.

It does, seem to be proprietary software.

[http://www.cutpress.eu/product/redsail-1360c-8/](http://www.cutpress.eu/product/redsail-1360c-8/)

It's probably a bad time, to suggest, anything else.

---

### Post by Jonny87 on 2011-11-20
> **hansdown said:**
> Hi, Jonny87.

It does, seem to be proprietary software.

[http://www.cutpress.eu/product/redsail-1360c-8/](http://www.cutpress.eu/product/redsail-1360c-8/)

It's probably a bad time, to suggest, anything else.

Yea thanks, I've got copies of the WinPC Sign and easycut that are mentioned in the article but they are windows apps and very outdated. I know I could try them in WINE, but would like to see if there is anything else first.

---

### Post by hansdown on 2011-11-20
I wish there was.

I work with a lot of industrial equipment.

I tend to stick with, CNC,Which does have linux alternatives.

Some of the others, I'd best not to discuss.

---

### Post by garyinspringhill on 2012-01-21
I developed tux plot and am looking for someone to test the imported usb cutters. If you want I can help you setup your cutter and add the results to the next release.
email [email]securetech@eastlink.ca[/email]

---

### Post by VetteGuy95 on 2012-01-24
> **garyinspringhill said:**
> I developed tux plot and am looking for someone to test the imported usb cutters. If you want I can help you setup your cutter and add the results to the next release.
email [EMAIL="securetech@eastlink.ca"]securetech@eastlink.ca[/EMAIL]

Will tux plot work with my [COLOR=Blue]**US Cutter Refine MH-721**[/COLOR] vinyl cutter?  Where can I preview this tux plot?

---

### Post by garyinspringhill on 2012-02-09
You can get tux plot at [securetech-ns.ca/camm-linux.html]("http://securetech-ns.ca/camm-linux.html")

---

### Post by syb3ria on 2012-10-20
Hello everybody. I own liyu sc1361 and would like to know if someone managed to run it work with latest inkscape and inkcut. I'm using 12.10 but can't work it out. Any help would be appreciated.

---

### Post by syb3ria on 2012-10-22
Ok, just letting you know how I fixed the problem i had.

After pluggung the plotter, I had to run this command via the termnal
```
sudo chmod 777 /dev/ttyUSB0
``` in order to gain permission using it, then I set up a new usb device, choosing generic driver, and raw type. When the new printer set up, I had to choose properties and change the URI from
```
serial:/dev/lp0
```
to
```
serial:/dev/ttyUSB0?baud=9600
```
Notice you have to add some code after the device URI in order to make it work properly.

Now asking for solution of another problem I'm facing... why inkscape and inkcut are adding some additional curves to the object I'm willing to cut out? When I'm ready to cut and I click on preview of inkcut, it opens a preview and I can see some lines added out of nowhere to the original design. Howit  could be fixed?

---

