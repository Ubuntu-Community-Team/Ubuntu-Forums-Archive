---
title: "Odd behavior from Update Manager, DeVeDe"
date: 2010-04-10
forum: General Help
---

### Post by sp0nge on 2010-04-10
Hello again! 

I have been having a frustrating issue with Ubuntu 9.04 on both my laptop and desktop machines for several days now. An Icon shows in the panel telling me there was a problem with updating. Attempts to update hangs on waiting for headers @ 99% but ultimately times out. I have not been able to update successfully for some time. 

Add to this the fact that DeVeDe will not respond. Trying to run DeVeDe from the Applications menu does nothing, running the program from the command line does nothing. Attempts to uninstall return this warning:

```
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 devede

```

Attempts to start Synaptic return this:

```
E: The package devede needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

```

I'm not sure what the problem is here, can anyone help me understand?

---

### Post by dcstar on 2010-04-10
> **sp0nge said:**
> Hello again! 

I have been having a frustrating issue with Ubuntu 9.04 on both my laptop and desktop machines for several days now. An Icon shows in the panel telling me there was a problem with updating. Attempts to update hangs on waiting for headers @ 99% but ultimately times out. I have not been able to update successfully for some time. 

Add to this the fact that DeVeDe will not respond. Trying to run DeVeDe from the Applications menu does nothing, running the program from the command line does nothing. Attempts to uninstall return this warning:

```
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 devede

```

Attempts to start Synaptic return this:

```
E: The package devede needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

```

I'm not sure what the problem is here, can anyone help me understand?

Change your repository to something else.

---

