---
title: "Take a screenshot of a java applet"
date: 2011-03-12
forum: General Help
---

### Post by diabolicalangle on 2011-03-12
Ok here's what I'd like to do:

Take a screenshot, or some other way of saving the visual output of a java applet ([http://www.nextbus.com/predictor/publicMap.shtml?a=georgia-tech&r=blue&d=Counterclo&s=nortavea](http://www.nextbus.com/predictor/publicMap.shtml?a=georgia-tech&r=blue&d=Counterclo&s=nortavea)), and saving that as an image, without having to manually do it (open browser go there, and take a screenshot).

I guess this would be most easily done using a script of some sort, but I have no idea how to go about doing this.. 

I would like to do this, so I can use this image to update my conky every 30 secs or so (got that part figured out :)). 

Any suggestions??

Thanks a ton!

---

### Post by lykeion on 2011-03-13
If the webpage doesn't have an API so that you programmatically can get an image, you'd still have to open a browser.
With that in mind you could create a script that would
* Open the page in a browser
* Save a screenshot image using ImageMagick/import (or any other screenshot grabbing with CLI)
* Close the browser

Suggestions:
Install **imagemagick** and use the *import* command to grab a screenshot
Maybe install **wmctrl** and use it to run the script in another workspace (don't know if it would work though)

---

