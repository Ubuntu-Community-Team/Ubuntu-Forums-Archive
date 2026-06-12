---
title: "Issue with NoIp IP updater"
date: 2012-02-24
forum: General Help
---

### Post by azmyth on 2012-02-24
I've been using the NoIP2 updater to update my IP for a few years. I manually downloaded it and installed. All of a sudden it stopped updating the IP so I figured I'd download/installed the noip2 package from synaptic. Now this doesn't work as well. I ran noip2 client in debug mode but it doesn't report any errors. It appears when you start noip2 it looks at your IP and then updates the hosts at the noip website. It then looks like it checks the IP every 30 minutes and if it changes it will update the IP otherwise it will just keep checking. Each time it says OK in the status in debug mode.

I log into the No IP website and it says last update was 2/9/12. This is a pain because I have to keep updating manually every 30 days. Anyone else seeing this?

---

### Post by azmyth on 2012-02-25
Hmm. guess the IP needs to change for the updater to update and reset the 30 day clock. Never realized that.

[http://www.no-ip.com/support/faq/EN/general/hosts-pending-deletion.html](http://www.no-ip.com/support/faq/EN/general/hosts-pending-deletion.html)

---

