---
title: "sync Nokia E63 with evolution under Lucid 10.04"
date: 2010-05-07
forum: General Help
---

### Post by peterr1028@gmail.com on 2010-05-07
This is my first post here.
Using 9.10, I was able to sync my Nokia E-63 after following the
instructions here
[https://help.ubuntu.com/community/NokiaEvolutionSyncing/Opensync](https://help.ubuntu.com/community/NokiaEvolutionSyncing/Opensync)
Since installing 10.04, syncml-obex-client seems to be missing. 
Does anyone now know of a way, (using 10.04), to sync the Nokia with evolution?
Many thanks for any help offered

---

### Post by Elfy on 2010-05-07
I think that you need one of these - [http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=all&keywords=libsyncml](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=all&keywords=libsyncml)

Moved from tutes'n'tips forum to a support forum.

I would also suggest asking if you can change your username as your e-mail will be harvested by bots.

---

### Post by jdpipe on 2010-10-28
Peter, I think you're right and somehow support has dropped off in Lucid 10.04. It possibly has been restored in 10.10 Maverick.

Here is the source package listing for the opensync syncml plugin:
[http://packages.ubuntu.com/source/maverick/libopensync-plugin-syncml](http://packages.ubuntu.com/source/maverick/libopensync-plugin-syncml)

And here is the binary package listing, which is clearly missing Lucid.
[http://packages.ubuntu.com/maverick/opensync-plugin-syncml](http://packages.ubuntu.com/maverick/opensync-plugin-syncml)

I found a related bug:
[https://bugs.launchpad.net/ubuntu/+source/libopensync-plugin-syncml/+bug/524938](https://bugs.launchpad.net/ubuntu/+source/libopensync-plugin-syncml/+bug/524938)

And here is an alternative package that you can try: "Genesis" together with "SyncEvolution":
[http://syncevolution.org/documentation](http://syncevolution.org/documentation)

Cheers
JP

---

