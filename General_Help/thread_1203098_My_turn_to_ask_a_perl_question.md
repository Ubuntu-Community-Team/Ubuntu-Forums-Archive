---
title: "My turn to ask a perl question"
date: 2009-07-02
forum: General Help
---

### Post by t4thfavor on 2009-07-02
OK, I am new to this perl thing, and I have been trying to write a daemon script to monitor my SIP/IAX2 trunks. That said, I would appreciate a little leniency in my coding technique.

I have some lines that look at "asterisk -rx "sip show registry" and iax show registry.

```

my $siptrunks = `/usr/sbin/asterisk -rx "sip show registry" | /bin/grep \"$_\" | awk '{print \$1}'`;
my $iaxtrunks = `/usr/sbin/asterisk -rx "iax2 show registry" |/bin/grep \"$_\" | awk '{print \$1}'`;

```

Which returns something like this

```

Host
my.hostname.net:5060
Host
1.1.1.1:4569

```

I only want to get back 

1.1.1.1:4569 and my.hostname.net:5060

now, I used awk to just get me the first field, what can I use to get rid of the "Host" that is returned with each one.

Would it be as simple as a sed 's/Host//g' or is there a better way to get what I want?

Karma don't fail me now!

TIA

Chance

---

### Post by KeyserSoze93 on 2009-07-03
you can add it to the awk command:

```
my $siptrunks = `/usr/sbin/asterisk -rx "sip show registry" | /bin/grep \"$_\" | awk '\$1!~/Host/{print \$1}'`;
```

which is basically "if the first field doesn't include Host".

---

### Post by t4thfavor on 2009-07-03
It appears to be exactly what I needed. While the sed command orks, it leaves me with a blank line where "Host" used to be. while this leaves me with just one line containing each host address.

Much appreciated.

Chance

---

