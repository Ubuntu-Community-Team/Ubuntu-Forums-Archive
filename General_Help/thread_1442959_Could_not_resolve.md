---
title: "Could not resolve"
date: 2010-03-30
forum: General Help
---

### Post by xXedixXx on 2010-03-30
Hello.

I use my netbook (Ubuntu 9.10) at school a lot and have to go through a proxy there, this works fine and I can use apt-get install and apt-get update there fine etc..

However when I get home and change my proxy settings to direct internet connection it's as if the synaptic side of Ubuntu ignores I've done this. My Chrome and Firefox web browser works fine once I change the proxy settings via "Network Proxy" but whenever I try to install new packages or updates I get messages like this: 

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata-java_2010g-0ubuntu0.9.10_all.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata-java_2010g-0ubuntu0.9.10_all.deb)
  Could not resolve &#8216;wf3.thegrid.org.uk&#8217;

As you can see it is trying to use a proxy to get the packages but it can't so it fails.

Does anyone know how to fix this? Thanks

---

### Post by xXedixXx on 2010-04-03
Bump.

Does anyone know how to solve this issue?

---

### Post by pastalavista on 2010-04-03
I can suggest opening System/Administration/Synaptic Package Manager and open the settings/preferences menu and under the network tab select 'direct connection to the internet' and if that doesn't work, try opening the settings/repositories menu, (also available in System/Administration/Software Sources), click the drop-down menu beside 'Download from:' Select 'other' and then click 'select best server'. It will look for the best/fastest connection for your locale. Hope this helps.

---

### Post by xXedixXx on 2010-04-04
Thanks for the reply, but after a couple of restarts and being used a lot more at home I think it has somehow sorted itself out :S

Thanks though!

---

