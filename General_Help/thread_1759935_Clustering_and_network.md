---
title: "Clustering and network"
date: 2011-05-16
forum: General Help
---

### Post by hanslammerts on 2011-05-16
Hi all,
 
I'm planning to build a 2-node LAMP cluster using Ubuntu and (if needed) KVM.
There's one important thing I still don't understand, however, and that is how I should configure my networking.
I would like to keep it as simple as possible, so what I have is two servers, one has one fixed network adapter and one wireless adapter, the other server has two wireless adapters (the last one will be placed in a spot in my house that does not allow for easy installment of network cables....)
Apart from the discussion whether wireless cards can be bridged or not, I would like to ask if the idea I'm having is even possible:
1) Is the number of fysical adapters in the two servers sufficient to build a cluster ?
2) Is the use of virtualization to be preferred (so you can add more virtual NICs, if needed) ?
3) I have read the following doc: [https://help.ubuntu.com/community/HighlyAvailableLAMP](https://help.ubuntu.com/community/HighlyAvailableLAMP) , that talks about using KVM. I can't figure out if the four NIC's that are shown in the picture are virtual ones or fysical ones. Has anyone used this howto ?
 
Hopefully you guys can give me a push in the right direction.
 
Thanks anyway,
Hans

---

