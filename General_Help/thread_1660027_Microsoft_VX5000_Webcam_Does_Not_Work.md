---
title: "Microsoft VX5000 Webcam Does Not Work"
date: 2011-01-04
forum: General Help
---

### Post by jereece on 2011-01-04
I plugged my Microsoft VX5000 Lifecam into my Ubuntu 10.10 system and expected it to fire up and work like a charm.  Well I had high hopes for the new year but I see it's not going to be easy.  I tried to use Skype and Camorama.  It just does not see the web cam.  When I plug it in, I see the little blue light come on for a second then go off.

Does anyone have any suggestions?

Thanks,
Jim

---

### Post by gordintoronto on 2011-01-04
This extract from Full Circle Magazine might help: (or maybe not?)

Q  My webcam worked in 10.04 but when I upgraded to 10.10 the kernel modules changed and the driver no longer worked.

A  Download the gspca-2.11.3.tar.gz tarball from the following gspca web site:
[http://moinejf.free.fr/](http://moinejf.free.fr/)
You might need to install build-essential using Synaptic.
Untar the file, then follow the readme instructions from the tarball:
Open a terminal, and cd to the directory where the make file is. Then:
make
sudo make install
Reboot to load the new modules. Run Cheese to confirm that it works.

---

