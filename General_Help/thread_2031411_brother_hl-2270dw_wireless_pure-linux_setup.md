---
title: "brother hl-2270dw wireless: pure-linux setup?"
date: 2012-07-21
forum: General Help
---

### Post by chogg on 2012-07-21
We recently purchased a Brother HL-2270dw: a nice b&w laser printer with automatic duplexing.  I installed the drivers without difficulty, and when I connect it using USB, it works beautifully.

The printer also has wireless capability.  So what I want is for it to get an IP address from our wireless router; then, I can add it over the network to my laptop.  The printer came with an installation CD and instructions for Windows and Mac.  But I don't have Windows or Mac!  Just a laptop and a desktop, both running Ubuntu 12.04.

It really should be possible to setup the wireless using only Ubuntu, right?  Has anyone attempted this?

We achieved a similar setup with the HP Deskjet 3050 J610.  But in that case, the printer can setup its own wireless network -- I could then attach to this network, access its settings through a browser window, and tell it the SSID and password for my router.  The Brother printer appears not to run a webserver, as far as I can see.

Thoughts?

---

### Post by Toz on 2012-07-21
According to: [http://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=2&ved=0CEwQFjAB&url=http%3A%2F%2Fwww.brother-usa.com%2FModelDocuments%2FConsumer%2FNetwork%2520Users%2520Manual%2FNUM_HL_2270DW_EN_2639.PDF&ei=pWkLUL_8L4rr0gGb2fzJAw&usg=AFQjCNFxE2leEXI5TMC7lExNkge65-eE-Q]("http://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=2&ved=0CEwQFjAB&url=http%3A%2F%2Fwww.brother-usa.com%2FModelDocuments%2FConsumer%2FNetwork%2520Users%2520Manual%2FNUM_HL_2270DW_EN_2639.PDF&ei=pWkLUL_8L4rr0gGb2fzJAw&usg=AFQjCNFxE2leEXI5TMC7lExNkge65-eE-Q"), it does run a web server. 

However, to access it, you need to be on a network. Can you plug it in wired to your router? By default the wired connection should be set for DHCP and it should get an ip address and allow you to access it so you can configure it for wireless.

---

### Post by searchfgold6789 on 2012-07-21
Read the Windows and/or Mac instructions. They will offer some hints.
I googled and skimmed a bit. It seems as if you can plug it into your router by a cable. Try plugging it in to the router, and then connecting to the printer and inputting the correct wireless settings.

---

### Post by chogg on 2012-07-23
Thanks for your advice!  Unfortunately, I can't seem to connect to the router.

When I plug in the ethernet cable, neither the printer's ethernet port nor the router's port "lights up".  But the wireless light on the back of the printer is lit up.  I see the button below which can be pushed by a pen tip, but pushing it only seems to initiate WPS (it prints out a piece of paper with a PIN).  My router doesn't have WPS capabilities.

Does anyone know a pure-hardware way to disable the wireless on the printer?  I read in the manual that wired and wireless can't be active at the same time, so I hope if I disable the wireless I can make a wired connection.

---

### Post by Toz on 2012-07-23
> Does anyone know a pure-hardware way to disable the wireless on the printer?

According to [http://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=2&ved=0CEwQFjAB&url=http%3A%2F%2Fwww.brother-usa.com%2FModelDocuments%2FConsumer%2FNetwork%2520Users%2520Manual%2FNUM_HL_2270DW_EN_2639.PDF&ei=pWkLUL_8L4rr0gGb2fzJAw&usg=AFQjCNFxE2leEXI5TMC7lExNkge65-eE-Q]("http://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=2&ved=0CEwQFjAB&url=http%3A%2F%2Fwww.brother-usa.com%2FModelDocuments%2FConsumer%2FNetwork%2520Users%2520Manual%2FNUM_HL_2270DW_EN_2639.PDF&ei=pWkLUL_8L4rr0gGb2fzJAw&usg=AFQjCNFxE2leEXI5TMC7lExNkge65-eE-Q"), page 28, the default setting for this printer is wireless disabled:
> If you want to switch the wireless network to enabled/disabled (disabled is the default), 


And according to [http://welcome.solutions.brother.com/BSC/public/as/sg/en/faq/faq/000000/000100/000005/faq000105_016.html?reg=as&c=sg&lang=en&prod=hl2270dw_all]("http://welcome.solutions.brother.com/BSC/public/as/sg/en/faq/faq/000000/000100/000005/faq000105_016.html?reg=as&c=sg&lang=en&prod=hl2270dw_all"), the process to reset the printer to defaults is:
> Using the control panel of the printer:

    Turn off the machine.
    Make sure that the front cover is closed and the power cord is plugged in.
    Hold down the Go button as you turn on the power switch. Keep the Go button pressed down until all the LEDs light up, and then the Ready LED turns off.
    Release the Go button. Make sure that all the LEDs turn off.
    Press the Go button six times. Make sure that all the LEDs light up to indicate the print server has been reset to its factory default settings. The machine will restart.

Maybe this will help get the wired connection working.

---

### Post by chogg on 2012-07-24
Yes, perfect!

So, to recap.  If you want to get your HL-2270DW on the network,

1) Reset the factory settings (if necessary) to enable wired ethernet

2) Connect the printer to your router via a cable

3) Find its IP address (e.g. using your router's DHCP client table)

4) Connect to the IP address and click "Network Configuration"  link (bottom of second column; username "admin" password "access" by default)

5) Enter your wireless network information and follow the instructions

---

### Post by Toz on 2012-07-24
Great. Please mark the thread as solved from the Thread Tools link above so that others can find and benefit from this solution. Thanks.

---

