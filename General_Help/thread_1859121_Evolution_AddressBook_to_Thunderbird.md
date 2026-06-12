---
title: "Evolution AddressBook to Thunderbird"
date: 2011-10-13
forum: General Help
---

### Post by ds_shellback on 2011-10-13
After trying the online converter link on the ubuntu help page:-

[URL="http://s"https://help.ubuntu.com/community/MigrateEvolutionToThunderbird[/URL]

I was a bit disconcerted to find that it's only a partial conversion and some contact information is dropped (Business address etc...). In fact, all the documented methods I found were limited to one degree or another. 

Evolution provides an address book conversion utility from which you can export a .csv file, but unfortunately thunderbird expects subtly different and re-ordered column data.

I've put together the following AWK program (my first AWK program - suggestions welcome) that translates the Evolution .csv file to one that will successfully import into Thunderbird. As Evolution allows up to four contact emails while Thunderbird allows only two; during the conversion process the first two contact email addresses are used. I find this a bit of an issue since many of the contacts in my address book have multiple email addresses, but I'm giving Thunderbird a go with 11.10 after a long time with Evolution.

Save this code to evototb.awk

```

BEGIN {
  FS="\",\"|\""
}
{
  gsub(/\\n/,",");
  print "\"" $2 "\",\"" \
  $3 "\",\"" \
  $2 " " $3 "\",\"" \
  $5 "\",\"" \
  $6 "\",\"" \
  $7 "\",\"\",\"" \
  $11 "\",\"" \
  $12 "\",\"" \
  $13 "\",\"" \
  $14 "\",\"" \
  $15 "\",\"" \
  $16 "\",\"" \
  $17 "\",\"" \
  $18 "\",\"" \
  $19 "\",\"" \
  $20 "\",\"" \
  $21 "\",\"" \
  $22 "\",\"" \
  $23 "\",\"" \
  $24 "\",\"" \
  $25 "\",\"" \
  $26 "\",\"" \
  $27 "\",\"" \
  $28 "\",\"" \
  $29 "\",\"" \
  $30 "\",\"" \
  $31 "\",\"" \
  $32 "\",\"" \
  $33 "\",\"" \
  $34 "\",\"" \
  $35 "\",\"\",\"\",\"\",\"\",\"" \
  $36 "\""
}

```

From the terminal here is the command sequence

Note.

The full path to evolution-addressbook-export will need to reflect the version you have installed.

Executing the evolution-addressbook-export command gives a known gLib warning; this doesn't prevent it generating the .csv file correctly!!!

```

/usr/lib/evolution/2.32/evolution-addressbook-export --format=csv --output=e-contact.csv

awk -f evototb.awk e-contacts.csv > tb-contacts.csv

```
 
You can now import the tb-contacts.csv file directly into Thunderbird.

Hope this helps

---

