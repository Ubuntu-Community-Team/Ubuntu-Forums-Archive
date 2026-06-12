---
title: "Where to get G'MIC repository authentication key?"
date: 2011-01-27
forum: General Help
---

### Post by Naggobot on 2011-01-27
Repository address for G'MIC can be found from

[http://gmic.sourceforge.net/repository.shtml](http://gmic.sourceforge.net/repository.shtml)

and is said to be

```
deb http://glouk.legtux.org/gmic_apt xxxx contrib

```

where xxxx = release i.e. lucid in the case of Ubuntu 10.04.

Does anyone know where to get authentication key for this repository or is it just not available?

---

### Post by Frogs Hair on 2011-01-27
If your are getting an error because of a missing software source , then you are unable to connect for some reason.

Make sure you have the correct package for your OS . The download page doesn't seem to helpful for information as to what releases are compatible.

---

### Post by Naggobot on 2011-01-27
G'MIC itself eems to work fine in Lucid from repository and it is possible install after the warning dialog has been accepted. 

So instructions  in 

[http://gmic.sourceforge.net/repository.shtml](http://gmic.sourceforge.net/repository.shtml)

advice to edit /etc/apt/sources.list file directly to set the repository. I used instead graphical tool from the Synaptic GUI. I also used GUI to install instead of using command line. 

Now GUI installation warns about the missing authentication and my guess was that this was because no PGP key was imported and due to this the Authentication section in the synaptic Settings->Repositories->Authentication does not list the repository as Authenticated. 

Of course this may be just a simple case of not understanding the system enough to understand it and due to this I see something missing when everything is in order.  So the fault may be caused by me not explicitly following the instructions.

---

