---
title: "python httplib, basehttpserver, ssl preshared keys"
date: 2011-08-02
forum: General Help
---

### Post by d3v1150m471c on 2011-08-02
I'm trying to write a p2p file sharing program using python's built-in libraries. Everything is going well. The only thing is that i'd like to be able to use openssl public and private keys so only a host with the public key could access/decrypt the filesharing. I've gotten these libraries (httplib, basehttpserver, ssl, os) to work using just a pem file containing both the public and private keys but no success with them seperately. Can someone point me in the right direction or offer an alternative? Thanks in advance :-)

PS, the goal of the project is to create an anonymous, decentralized, secure file sharing program. I want to be able to upload this to sourceforge so everyone can use it, if that's any incentive :-)

---

### Post by LemursDontExist on 2011-08-03
> **d3v1150m471c said:**
> I'm trying to write a p2p file sharing program using python's built-in libraries. Everything is going well. The only thing is that i'd like to be able to use openssl public and private keys so only a host with the public key could access/decrypt the filesharing. I've gotten these libraries (httplib, basehttpserver, ssl, os) to work using just a pem file containing both the public and private keys but no success with them seperately. Can someone point me in the right direction or offer an alternative? Thanks in advance :-)

PS, the goal of the project is to create an anonymous, decentralized, secure file sharing program. I want to be able to upload this to sourceforge so everyone can use it, if that's any incentive :-)

A little more detail would be useful.  

In a p2p connection, if both parties want to be able to send and receive encrypted data, they'll both need public and private keys...

Possibly what you want is for users to generate their own key pairs, and then transmit the public key to the other party to allow for encryption?  I'm not a crypto expert, but I think having a single key pair for a network really only makes sense if there's a central server.

---

### Post by d3v1150m471c on 2011-08-03
i might just skip the entire p2p procress and go with a decentralized filesharing network. something like tor or i2p but my own implementation because that will benefit the anonymity greatly. the problem i was running into btw was not with using ssl on a python server, that worked fine, but when i split the pem file into a public and private key and tried to connect to the server while loading the public key in the client side i get a failure.

---

