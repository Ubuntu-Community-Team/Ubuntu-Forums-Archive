---
title: "Learning Curve Advice"
date: 2009-08-22
forum: General Help
---

### Post by jmlee320 on 2009-08-22
Looking for any and all recommendations in terms of increasing my Linux/Ubuntu skills as quickly as possible.

Here is where I am @ currently:

I am the sysadmin, among other things, for a small start-up.  I am somewhat well-versed in Windows networking but only using workgroups, none in an actual domain.  Nothing in a server environment.  Which I guess means i'm not really that well versed, but anyway...

I am maintaining a Windows workgroup network with 9 client machines, 3 Windows Vista, 6 WIndows XP, 4 network printers/scanners and a Windows XP box as a file server.  However, we have grown to where we have reached the 10 device connection limit of XP.

In looking for a server solution to this problem, cost for a start-up being a primary concern, I turned to open source.

I'm basically in proof concept phase w/ a Ubuntu 8.04 LTS server I now have set up on my network as a file server.

I'm using Webmin and PuTTY to administer the server.  What I have set up in terms of file sharing looks like this:

/shares/share_one (public share)
/share/share_two (somewhat restricted share)
/share/share_three (private share)

3 users for each share, each appropriate  user owns each share.  Set up my shares in Samba via Webmin, I can now map drives to my client machines as is appropriate depending on the user.  I've demonstrated the stability of the config already with a couple of test drives mapped from XP machines on the network.

I'm really, really pleased with the results.

So, realizing that open source, if nothing else based on cost alone, will be a large part of my organizations' future, my question after that wall of text is this:


Is the LPI/Ubuntu certification trail the best way for me to get smart fast?

I'm currently using [http://www.borders.com/online/store/TitleDetail?sku=1590599233](http://www.borders.com/online/store/TitleDetail?sku=1590599233) to bolster my fail when I hit a stumbling block, but i'm not blown away.

If the LPI/Ubuntu certs are a good way to achieve competence, is something like [http://www.borders.com/online/store/TitleDetail?view=2&type=0&catalogId=10001&simple=1&rpp=25&defaultSearchView=List&keyword=linux+LPI&LogData=[search%3A+24%2Cparse%3A+35]&searchData={productId%3Anull%2Csku%3Anull%2Ctype%3A0%2Csort%3Anull%2CcurrPage%3A1%2CresultsPerPage%3A25%2CsimpleSearch%3Atrue%2Cnavigation%3A0%2CmoreValue%3Anull%2CcoverView%3Afalse%2Curl%3Arpp%3D25%26view%3D2%26all_search%3Dlinux%2BLPI%26type%3D0%26nav%3D0%26simple%3Dtrue%2Cterms%3A{all_search%3Dlinux+LPI}}&storeId=13551&sku=0596005288&ddkey=http:SearchResults]("http://www.borders.com/online/store/TitleDetail?view=2&type=0&catalogId=10001&simple=1&rpp=25&defaultSearchView=List&keyword=linux+LPI&LogData=%5Bsearch%3A+24%2Cparse%3A+35%5D&searchData=%7BproductId%3Anull%2Csku%3Anull%2Ctype%3A0%2Csort%3Anull%2CcurrPage%3A1%2CresultsPerPage%3A25%2CsimpleSearch%3Atrue%2Cnavigation%3A0%2CmoreValue%3Anull%2CcoverView%3Afalse%2Curl%3Arpp%3D25%26view%3D2%26all_search%3Dlinux%2BLPI%26type%3D0%26nav%3D0%26simple%3Dtrue%2Cterms%3A%7Ball_search%3Dlinux+LPI%7D%7D&storeId=13551&sku=0596005288&ddkey=http:SearchResults") worthwhile?

Any and all advice is welcome.

---

### Post by wojox on 2009-08-22
I have both those books as well. They help a lot. The LPI is good to learn because you need two certifications from them before you can take the UCP test.

---

