---
title: "Can't forward printer port to test machine"
date: 2011-02-19
forum: General Help
---

### Post by DasherDooDad on 2011-02-19
I'm using a laptop running Ubuntu 10.04.
A printer is connected to the USB port.
I'm using SSH to connect to a test machine running Ubuntu 10.10.
I want to forward the printer-port to the test machine, so when I log into it from my laptop, I can print a file and it will come out on the printer attached to my laptop.
Here is the command I try:

        ssh -g -R 631:localhost:880 ...

This would forward printing from the test machine to the CUPS server on my laptop, and then to the printer.
Here is the message I get after connecting:

       Warning: remote port forwarding failed for listen port 631

What am I missing?
I've googled all over the intenet; people say you can do it, but omit enough of the details that I can't tell whether they ever got it working or not.

---

### Post by DasherDooDad on 2011-02-21
Ok -- the deal is that the remote port is the first parameter:

ssh -R 8801:localhost:631 ...

The I can print from the remote host using

lpr -H localhost:8801 -P HomePrinter <file>

The formatting is poor but I can work on that separately.

---

