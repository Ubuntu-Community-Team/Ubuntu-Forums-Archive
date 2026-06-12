---
title: "Displaying OS Version in AD"
date: 2012-07-19
forum: General Help
---

### Post by kalanis on 2012-07-19
We are customizing Ubuntu 11.04 and giving updates once a month. In  order to keep track of the Updated Version, we are changing the  Distribution Release parameter in lsb-release. Currently we are using  Power Broker Identity Services Open 7 version (previously known as  Likewise) to connect to Windows Active Directory. The the Active  Directory Operating Systems tab, Version parameter correctly reflects  the changed Distribution Release parameter once it's added to domain.

But  the problem arises if we do a change in the Distribution Release  parameter, when it is already in the domain. The information does not  get correctly updated in the Active Directory. We tried deleting cache  and refreshing PBIS services as well. But still the data did not get  correctly reflected in AD.

Would appreciate any thoughts on how to resolve this from Ubuntu, Likewise users.

---

