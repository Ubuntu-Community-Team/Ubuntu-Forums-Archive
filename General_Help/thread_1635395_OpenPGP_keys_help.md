---
title: "OpenPGP keys help"
date: 2010-12-01
forum: General Help
---

### Post by COKEDUDE on 2010-12-01
I am trying to add a OpenPGP key for launchpad. It said to use this command. 
```
gpg --fingerprint
```

When I use that command nothing shows. 

Next I clicked on the the How to get the fingerprint. It said to go into Passwords and Encryption Keys. Then the My Personal Keys tab. I have nothing there. What should I do to get something there?

---

### Post by czr114 on 2010-12-01
Are you trying to load someone else's key into your gpg or are you trying to export your public key to Launchpad?

If you're trying to import, you use 'gpg --import <filename>' to import from a local file, or 'gpg --recv-keys <key ID>' to receive from the public keyservers.

If you're trying to export your public key, first find the key ID with 'gpg --list-keys', then run 'gpg --export -a --output <output filename> <key ID>'

These functions are more straightforward in Seahorse (Applications -> Accessories -> Passwords and Encryption Keys -> Tab to My Personal Keys).


If nothing shows in 'gpg --fingerprint', then you have neither public nor private keys in your local gpg database. If you're importing a key, it's not there, and if you're trying to export, then you don't yet have a personal keypair.

---

### Post by COKEDUDE on 2010-12-02
I'm trying to create my own key to use in Launchpad. I have no idea how to do that. Could you please explain how to do that?

---

### Post by czr114 on 2010-12-02
'gpg --gen-key'

The options can be a bit in-depth. There are some great resources on the web and in the man pages for explaining these in details, but here are the selections I used:

1 (RSA and RSA)
4096
5y
<name>
<email>
<comment>
o (okay)
<password> (use a strong password)


With that, you're done. Make a note of your key ID (the main, not the sub). This is how you will reference that keypair in the future.

If you want, you can invoke 'gpg --edit-key <key ID>' to set preferences, such as:

gpg --edit-key <key ID>
setpref S9 S10 S8 S7 S4 H10 H9 H8 H11 H2 Z3 Z2 Z1
save

That's an optional step, but it's what I did.

Now you want to mark that key as primary:

gpg --edit-key <key ID>
uid 1
primary
quit

Now, you have to export it: 'gpg --export -a --output <output filename> <key ID>'

If you want, you can add this new key to the public keyservers with: 'gpg --send-key <key ID>'

This is your public key. This exported file is what you share.

I also set 'GPGKEY=<key ID>' in my .bash_profile to make it easier to call from the command line (even though my ID is rather memorable).

Now that you're up and running with gpg, I strongly suggest you set up your key in your MUA of choice. For Thunderbird, open Synaptic, and install the 'enigmail' package.

If you need help setting up enigmail, I can help you with that, too.

GPG is based on the OpenPGP standard which is in wide use in the Linux community. Secure, reliable, and authenticated email is a killer feature which needs wider adoption.

---

### Post by COKEDUDE on 2010-12-02
Thank you for the great guide. Could you please explain how to set up Thunderbird with enigmail?

---

### Post by COKEDUDE on 2010-12-10
Could you anyone explain how to set up Thunderbird with enigmail?

---

### Post by COKEDUDE on 2010-12-11
> **COKEDUDE said:**
> Could you anyone explain how to set up Thunderbird with enigmail?

Does anyone know?

---

