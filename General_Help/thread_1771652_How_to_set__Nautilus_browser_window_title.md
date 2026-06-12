---
title: "How to set  Nautilus browser window title"
date: 2011-05-30
forum: General Help
---

### Post by rquint on 2011-05-30
I have a little nautilus script to open a browser window as root

```

#!/bin/bash

gksudo nautilus $NAUTILUS_SCRIPT_CURRENT_URI

```

which I'd like to modify to include the  extra text "(as root)" in the window title.  I've searched through gconf without finding anything and done a Google search where I found scripts for terminal windows, but the option used there to set the window title don't work with nautilus.  BTW the same script on a machine running Debian Squeeze automatically did a similar thing without any intervention by me.  Anyone know how to do this or where I can look for an example?

---

### Post by L a r r y on 2011-10-18
> **rquint said:**
> I have a little nautilus script to open a browser window as root

```

#!/bin/bash

gksudo nautilus $NAUTILUS_SCRIPT_CURRENT_URI

```

which I'd like to modify to include the  extra text "(as root)" in the window title.  I've searched through gconf without finding anything and done a Google search where I found scripts for terminal windows, but the option used there to set the window title don't work with nautilus.  BTW the same script on a machine running Debian Squeeze automatically did a similar thing without any intervention by me.  Anyone know how to do this or where I can look for an example?

Hello everyone,
This poster has asked a question that I was hoping to find an answer to.

In my case, I open a local folder to the public_html folder of my local Web server.  The page is titled "public_html."  I open a remote connection to my web site on the Internet, in Nautilus, and that window is called "public_html," also.

This caused me some confusion one day as I had these two windows, and after updating a file locally I was to post it on the web site; I did just the opposite and wiped out my changes!

I get to the remote public html by using a bookmark with my website domain as its name, and it would be nice to be able to see that in the window title.

If I take the time, I can move left on the breadcrumb trail and either arrive at /home or at example.com, in the order of local, remote.

If anyone has the answer to o.p's adding (as root) it might also serve my purpose.

Thanks

10.04 Ubuntu running here.
Larry

---

