---
title: "HELP loads of errors when ever i try and install updates etc"
date: 2009-09-23
forum: General Help
---

### Post by kerileigh on 2009-09-23
When ever i run updates etc i get all these errors

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6B15AB91951DC1E2
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://deb.opera.com](http://deb.opera.com) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F9A2F76A9D1A0061

W: Failed to fetch [http://deb.opera.com/opera/dists/stable/Release](http://deb.opera.com/opera/dists/stable/Release)  

W: Failed to fetch [http://deb.opera.com/opera-beta/dists/stable/non-free/binary-i386/Packages](http://deb.opera.com/opera-beta/dists/stable/non-free/binary-i386/Packages)  404 Not Found

W: Some index files failed to download, they have been ignored, or old ones used instead.


I just don't understand what its telling me or how to fix it :confused::confused::confused::confused:

Any help or advice appriciated

thanks
Keri

---

### Post by zkriesse on 2009-09-23
What's it is telling you is that there isn't verification for certain repositories on the system. Repositories are what all the updates and programs "come from." It's also telling you that there isn't verification for the GPG key. Must have been something you downloaded but not the key. You could re-install or repair using the cd but other than that I'm not sure.

---

### Post by nothingspecial on 2009-09-23
Open gedit, the text editor and copy this into it

```
-----BEGIN PGP PUBLIC KEY BLOCK-----
Version: GnuPG v1.4.1 (GNU/Linux)

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
=wGGg
-----END PGP PUBLIC KEY BLOCK-----
```

save it as key.txt

In your menu goto system > administration > software sources and click on the authentication tab. Then click on import key file.

Navigate to your previously saved key.txt

Then click reload.

A pointy clicky answer - cool

---

### Post by P4man on 2009-09-23
> **kerileigh said:**
> When ever i run updates etc i get all these errors

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6B15AB91951DC1E2
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://deb.opera.com](http://deb.opera.com) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F9A2F76A9D1A0061

W: Failed to fetch [http://deb.opera.com/opera/dists/stable/Release](http://deb.opera.com/opera/dists/stable/Release)  

W: Failed to fetch [http://deb.opera.com/opera-beta/dists/stable/non-free/binary-i386/Packages](http://deb.opera.com/opera-beta/dists/stable/non-free/binary-i386/Packages)  404 Not Found

W: Some index files failed to download, they have been ignored, or old ones used instead.


I just don't understand what its telling me or how to fix it :confused::confused::confused::confused:

Any help or advice appriciated

thanks
Keri

Perhaps its semantics but those are not errors but warnings (W). consider them 'for your information". It doesn't hurt to cure them, but not curing them won't prevent anything from working. 

You added third party repositories (mostly for Opera) but you didn't import the keys so apt can verify the source. Follow nothing special's post to fix at least one of them (not sure which). It also appears Opera's repository for ubuntu isn't working right now, at least I don't see any repo for ubuntu anymore. Im not sure if thats only temporarily, but if not, you can remove those software sources from system > administration > software sources

---

### Post by dumblebee100 on 2009-09-23
> **kerileigh said:**
> When ever i run updates etc i get all these errors

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6B15AB91951DC1E2
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://deb.opera.com](http://deb.opera.com) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F9A2F76A9D1A0061

W: Failed to fetch [http://deb.opera.com/opera/dists/stable/Release](http://deb.opera.com/opera/dists/stable/Release)  

W: Failed to fetch [http://deb.opera.com/opera-beta/dists/stable/non-free/binary-i386/Packages](http://deb.opera.com/opera-beta/dists/stable/non-free/binary-i386/Packages)  404 Not Found

W: Some index files failed to download, they have been ignored, or old ones used instead.


I just don't understand what its telling me or how to fix it :confused::confused::confused::confused:

Any help or advice appriciated

thanks
Keri

regarding the public key issue 
u can use this command instead of searching for keys in launchpad ..it takes lots of time 
so use this instead
```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com keyvalue
```

replace the keyvalue with the code u get ..in your case keyvalue is F9A2F76A9D1A0061 and 6B15AB91951DC1E2 respectively

---

### Post by kerileigh on 2009-09-27
thanks for the replies i shall have a work through the things you have mentioned and let you know how i get on :KS

---

### Post by kerileigh on 2009-09-27
I did what you said with the text file, although it wouldn't let me reload it just wanted to close. I ran updates afterwards and got jsut this warning

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6B15AB91951DC1E2

It came forward with  9mb update for opera which i installed successfully it would appear.

When you say load stuff off a cd what do you mean?

Will dumblebee100's way get me the other public key?

---

### Post by kerileigh on 2009-09-27
Hello all seems to be ok now.

I took nothing special's advice for the first key and dumblebee's advice for the second and now seem to get no (w)'s.

Thankyou very much to everyone.

Hopefully next time i might be able to sort the problem myself :KS:KS

---

