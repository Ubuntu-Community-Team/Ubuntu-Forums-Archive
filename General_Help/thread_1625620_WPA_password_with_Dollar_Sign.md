---
title: "WPA password with Dollar Sign"
date: 2010-11-19
forum: General Help
---

### Post by bakegoodz on 2010-11-19
I'm trying to setup a linux computer to connect to my works wirless. It uses a WPA2 password with a dollar sign in it. I can't input it into wpa_passphrase because it thinks dollar sign means some command.

How do I tell it that the dollar sign is part of the password?

---

### Post by coffeecat on 2010-11-19
I'm not familiar with this app:

> **bakegoodz said:**
>  wpa_passphrase

Do you mean the network manager window for the passphrase?

Anyway, try escaping the $ with a backslash. Instead of "some$passkey", use "some\$passkey".

---

### Post by prshah on 2010-11-19
> **bakegoodz said:**
> can't input it into wpa_passphrase because it thinks dollar sign means some command.
How do I tell it that the dollar sign is part of the password?

As suggested, "escape" the $ sign, ie, replace $ with \$ or place the entire passphrase in double quotes. ```
Fri Nov 19 22:02:43 ~:$ wpa_passphrase somessid "test&pass"
network={
	ssid="somessid"
	#psk="test&pass"
	psk=db1c8e0073f0870c8d9e0fdd276125887ad20876c4f0500f63733331ed26b3d1
}
Fri Nov 19 22:02:49 ~:$ wpa_passphrase somessid test\&pass
network={
	ssid="somessid"
	#psk="test&pass"
	psk=db1c8e0073f0870c8d9e0fdd276125887ad20876c4f0500f63733331ed26b3d1
}

```

Both have the same result.

---

### Post by bakegoodz on 2010-11-19
It was the exclamation in the password messing it up. Quotes didn't work, but \! did. Thanks Everyone!

---

