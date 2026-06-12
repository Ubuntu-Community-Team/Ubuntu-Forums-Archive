---
title: "How to backup/reimport GPG keys.."
date: 2011-10-02
forum: General Help
---

### Post by MG&amp;TL on 2011-10-02
Hi, I need to have GPG keys on my computer, to sign debian packages and contribute to launchpad.

However, on the (frequent) occasions I need to reinstall, generally I have to regenerate a GPG key, load it to the keyserver, then persuade launchpad to take the new key.

Is there a way to export the GPG key (say to a USB or Ubuntu One), then reimport as if it was the key I'd generated.

---

### Post by haqking on 2011-10-02
> **MG&TL said:**
> Hi, I need to have GPG keys on my computer, to sign debian packages and contribute to launchpad.

However, on the (frequent) occasions I need to reinstall, generally I have to regenerate a GPG key, load it to the keyserver, then persuade launchpad to take the new key.

Is there a way to export the GPG key (say to a USB or Ubuntu One), then reimport as if it was the key I'd generated.

file export, file import ;-)

---

### Post by MG&amp;TL on 2011-10-02
Errr...which files? Is there something in the passwords/encryption keys dialogue? God I'm thick this morning. Thanks, haqking. ;)

---

### Post by haqking on 2011-10-02
> **MG&TL said:**
> Errr...which files? Is there something in the passwords/encryption keys dialogue? God I'm thick this morning. Thanks, haqking. ;)

Depending what tool you use, probably seahorse (passwords and encryption keys) highlight your key, file menu>export then put the .asc file where you like ;-)

---

### Post by MG&amp;TL on 2011-10-02
Thanks haqking. Being thick after all.

---

### Post by haqking on 2011-10-02
> **MG&TL said:**
> Thanks haqking. Being thick after all.

ha ha no worries, i miss the obvious all the time ;-)

Peace

---

### Post by MG&amp;TL on 2011-10-02
Errr...haqking. I have the .asc file, and I've imported it. However, it's put it under 'other keys' section. It says I need to sign it to show that I trust it, not just enter the password. And will it then be 'mine'?

---

### Post by haqking on 2011-10-02
> **MG&TL said:**
> Errr...haqking. I have the .asc file, and I've imported it. However, it's put it under 'other keys' section. It says I need to sign it to show that I trust it, not just enter the password. And will it then be 'mine'?

did you have personal keys highlighted when you imported ?

and yes you have to trust a key

---

### Post by MG&amp;TL on 2011-10-02
Can I then use it to sign things as if I generated said key?

---

### Post by haqking on 2011-10-02
> **MG&TL said:**
> Can I then use it to sign things as if I generated said key?

well you did generate it didnt you ?

If the key is on your system and you trust it then yes you should be able to configure your email or folder encryption or whatever key it is to sign or encrypt.

Try it ;-)

---

### Post by MG&amp;TL on 2011-10-02
Thank you. :)

It's generating another key now. I just wanted to check, as generating a key is a twenty-minute job on my old and beloved rustbucket.

---

### Post by dave01945 on 2011-10-02
I think the export in password and encryption keys only exports the public key and that is no good without the private key to export private key you need to do

```
gpg --list-secret-keys
```

that will give you the key id then with that you need to do

```
gpg --output <outfile> --armor --export-secret-key <key_identifier as gleaned from above>
```

or you can just copy the directory

```
~/.gnupg
```

that contains private and public keys whatever you find easier i usually use the second then i can just copy the whole directory back after install and it's exactly as it was before

---

### Post by haqking on 2011-10-02
> **MG&TL said:**
> Thank you. :)

It's generating another key now. I just wanted to check, as generating a key is a twenty-minute job on my old and beloved rustbucket.

why you generating a new one ? i thought you already had the keys and was just importing them ?

---

### Post by MG&amp;TL on 2011-10-02
Because it said that it needed another key to sign the original.

It's a bit late now, :D but never mind, I can always re-sign the debian package.

---

### Post by haqking on 2011-10-02
> **MG&TL said:**
> Because it said that it needed another key to sign the original.

It's a bit late now, :D but never mind, I can always re-sign the debian package.

oh ok.  well at least your back to solved again ;-)

cheers

---

