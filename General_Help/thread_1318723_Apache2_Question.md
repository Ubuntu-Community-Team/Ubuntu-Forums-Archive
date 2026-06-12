---
title: "Apache2 Question"
date: 2009-11-07
forum: General Help
---

### Post by DBish225 on 2009-11-07
I have three different sites configured with different domains on my server. The root directory for each site is set up like "/var/domain.com". I would like to install phpbb on this server and allow it to be accessible by each of the domains. The problem is, phpbb installs to "/var/www/phpbb", which is not the root directory for any my sites. I want to configure my sites so when a user types "domain.com/phpbb" they go to the "/var/www/phpbb" directory. I dont neccessarily need to have three seperate forum sites, just one will work fine for all the domains. Thanks in advance for any suggestions!
-DBish225

---

### Post by Maheriano on 2009-11-07
Change your domains to var/www/domain. That's the way I have mine set up and I have 2 PHPBB3 installs.

---

### Post by DBish225 on 2009-11-07
Thanks, I've changed the sites to be located in "/var/www/domain.com/" now. How would I install separate phpbb for each site?

---

### Post by DBish225 on 2009-11-07
I was able to figure it out on my own. I basically have to install phpbb on each site manually(downloading the install files then uploading them where I want them on the server), instead of doing it via terminal.

---

### Post by Maheriano on 2009-11-09
> **DBish225 said:**
> I was able to figure it out on my own. I basically have to install phpbb on each site manually(downloading the install files then uploading them where I want them on the server), instead of doing it via terminal.

Ya that would do it. There might be some sort of multi install where you can use the same database for each one but I haven't come across anything like that. I just use separate everything.
Check out all the addons for PHPBB3, I've got a bunch on my installs.

---

### Post by Johnsie on 2009-11-09
sorry, I posted an idea and then realised it wouldn't work: 

Create a file called index.php where you want the forum to appear to be.

use the  follwing line of code in it:

include('location of phpbbs actual index.php');

---

