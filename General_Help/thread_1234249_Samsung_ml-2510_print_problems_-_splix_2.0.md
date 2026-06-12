---
title: "Samsung ml-2510 print problems - splix 2.0"
date: 2009-08-07
forum: General Help
---

### Post by hubiedo on 2009-08-07
SEE MOST RECENT NOTES FOR OUTCOME AND REASONS AT THE BOTTOM.

recently i have spent considerable time fixing my printer problems and hope this helps someone else down the road. i installed a new mobo and printing suddenly went upside down. using lpt port for samsung ml-2510. i called samsung after 2 weeks and they finally said no support for linux. the problem was that on initial boot the printer worked fine from ubuntu 8.04 printer configuration. after a few minutes or an hour or so it would crash the system when i sent something to it and the best i could tell it was like if it used the power save feature it wouldn't print. 

the error page it printed was 

Internal error= false
position: 0x909f (370023)
system: h6fwsim_snipe/xl_image
version: SPL 5.07 06/27-2006

the system worked fine on prev mobo and printing was good. 

on the new mobo the samsung configurator never was able to find, install, and successfully test the printer. i bet i crashed / system went down & rebooted 2 -3 times a day trying all this stuff. i reinstalled all cups, changed the power save, tried new parallel print port card, installed and reinstalled printers etc. all no go! after continually searching the net i found a mention for a different printer to install splix 2.0.

i thought the solution was the splix 2.0 that i downloaded from softpedia(?)

here are the general steps:

download the splix 2.0.0
unpack the file w/ archive manager
**** READ THE INSTALL TEXT--- IT WORKS****
my [http://localhost:631](http://localhost:631) still doesn't work - not sure why but continued working with it
deleted all the printers
reinstalled the ubuntu printers - tested fine as usual
went to Samsung configurator it showed two printers - not sure how i managed - that tested one no go - tested the other and it worked and printed a cups test page for the first time in 3-4 weeks 

i left the system alone for 4-5 hours and it still prints and no crashes so far. 

it also supports some dell & ibm printers. it appears that they have added the newer printers to this version of splix.

here is splx page:
[http://splix.ap2c.org/](http://splix.ap2c.org/)


OOPS! tried to print this page and it crashed again.

does anyone have any ideas?

it appears?? if i turn the printer off / on before i print it will function fine for a while -not sure if this indicates true problem related to power save.

update: 08/27/09 

turning off the printer didn't work; took the printer for service printer was fine. my final conclusion is the printer won't work with this mobo. ordered a new printer!! i have tried other printers and they work fine but not the ml-2510 samsung. the new mobo is asus m3a78-emh hdmi.

---

