---
title: "Simple BASH script question.. auto-fill"
date: 2010-07-01
forum: General Help
---

### Post by DJYoshaBYD on 2010-07-01
Hola, all...

I work in networking, and use linux all the time for troubleshooting stuff.. I have to use SSH to log into our shadow routers and whatnot..

i have a script, to where i dont have to type in the whole command to log in.. its like this (no.. this not it.. but i cant post the IP and port and stuff.. lol)


```
ssh user@1.1.1.1 -p 1234
```

that is named router, and placed in my bin (or sbin.. i cant remember), so that i can run it anywhere..

the thing is, it prompts me for my password..

now, im not worried about security, as I work in a VERY secure building, and im on an MPLS VPN.. lol.. nothing is getting in..

but to streamline my work, i would like to just type on word, and have it log into whatever i need..

so.. if it asks me for a password, like this

```
Password? 
```

then how do I tell my script to auto-fill my password?

it can be stored in plain text within the text script.. again, we are very secure, so that is not an issue.. 

like, do I echo it or something?

any help would be appreciated, cause i havent really found anything that helps.. lol

thanks

---

### Post by weemadarthur on 2010-07-01
You can set up ssh to login using public keys instead of passwords, if the remote host supports it.

Try searching Google for "ssh public key authentication" or "ssh without password"

---

### Post by justleen on 2010-07-01
ssh can only use key based authentication to get "passwordless" logins.

Whether you can use this method depens on the server-side you connect to.
If you ssh into "hardware" routes/vpn/ilo/etc  you usually will have to add the keys by hand - how to do that would be descriped in the manufacturers manuals/docs.

If you need to connect to a linux server, its easier.
Generate private keys
```
 ssh-keygen
```
Then copy those over to the remote host (you can do this manually,but ssh comes with a nice tool for it nowadays)
```
 ssh-copy-id user@remote.host 
```

If you login with a different id on the remote side, you still copy your own userkeys.'
so as "user" logging in as "root@server", you would generate keys as "user" and use "ssh-copy-id root@server"

Ps: leave the passphrase empty when generating keys, otherwise it will prompt for that...

---

