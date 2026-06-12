---
title: "Dansguardian Filter Lists Username Transfer  Problem"
date: 2010-02-19
forum: General Help
---

### Post by azecraze on 2010-02-19
Hello,
I am running Ubuntu Linux 7.10 with DansGuardian 2.10.1.1 as per the setup shown on another thread here by me.

I have been running DG for a long time in single user mode, and decided to upgrade to filter groups.
However, I have come up with a problem in that DG is not recognising the authenticating username to send the user to the correct group. No matter what username I add to the filtergroupslist, it always sends it thru to the default group(f1). Meaning that it is not receiving the username info,correct?

I have a separate physical proxy server handling authentication and then redirecting thru to the DG box, and then on to the internet. This means that the server with DG on does not handle authentication. 

1. Is the username supposed to be carried over to the DG box in the http header from the originating server, or does it stop when it leaves the originating proxy server?

2. How do I get DansGuardian to see the username info from the originating proxy server?

3. As I understand it from reading HEAPS of stuff, I dont need to do anything to Squid as part of this process, because I dont need to set up using the "Sandwich" method - isnt DG supposed to handle this independently?

I need to keep the proxy server on the front end because it handles user specific whitelists for me that DG and Squid cant handle.

---

