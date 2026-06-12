---
title: "vCard &amp; awk"
date: 2009-11-08
forum: General Help
---

### Post by WhiskyChris on 2009-11-08
I'm trying to create a basic awk script to take some details from a vcard file. I'm not sure where the problem arises but when trying to produce an output of the form

Name,email

it appears that the email is over typing the name... Below is my awk script, an example vcard file and the output - any help would be much appreciated!

Awk Script - vcard.awk
```
BEGIN { FS = ":"; OFS = "," }

/^BEGIN/ {
    name = ""
    email = ""
}

/^FN/ {
# handle name here
name = $2
}

/^EMAIL/ {
#handle email here
email = $2
}

/END/ {
# print output
print name, email
}
```

Output
```
(bin) highlandPark $ gawk -f vcard.awk ../Desktop/contacts.vcf
,a.n.email@host.com
,anne@other.com

```

vCard file - contacts.vcf
```
BEGIN:VCARD
VERSION:3.0
REV:2009-11-08T18:37:18Z
UID:pas-id-4AF70FDE00000003
TEL;TYPE=CELL;X-EVOLUTION-UI-SLOT=3:0123456789
EMAIL;TYPE=HOME;X-EVOLUTION-UI-SLOT=2:a.n.email@host.com
X-MOZILLA-HTML:FALSE
X-EVOLUTION-VIDEO-URL:
FBURL:
CALURI:
X-EVOLUTION-BLOG-URL:
X-EVOLUTION-FILE-AS:Person\, A
N:Person;A;;;
FN:A Person
NOTE:
X-EVOLUTION-SPOUSE:
NICKNAME:
X-EVOLUTION-ASSISTANT:
X-EVOLUTION-MANAGER:
ROLE:
TITLE:
URL:
END:VCARD

BEGIN:VCARD
VERSION:3.0
REV:2009-11-08T18:37:42Z
UID:pas-id-4AF70FF600000004
TEL;TYPE=CELL;X-EVOLUTION-UI-SLOT=3:0987654321
EMAIL;TYPE=HOME;X-EVOLUTION-UI-SLOT=2:anne@other.com
X-MOZILLA-HTML:FALSE
X-EVOLUTION-VIDEO-URL:
FBURL:
CALURI:
X-EVOLUTION-BLOG-URL:
X-EVOLUTION-FILE-AS:Other\, Anne
N:Other;Anne;;;
FN:Anne Other
NOTE:
X-EVOLUTION-SPOUSE:
NICKNAME:
X-EVOLUTION-ASSISTANT:
X-EVOLUTION-MANAGER:
ROLE:
TITLE:
URL:
END:VCARD
```

---

### Post by DaithiF on 2009-11-08
works ok for me, so i suspect your contacts.vcf file is from windows and therefore has windows style line endings \r\n.  the \r gets left at the end of the lines and when output causes the 'cursor' to reset to the start of the line when printing.

so you need to convert to unix line endings ... either the special-purpose dos2unix command, or just doing it yourself in sed ...
```
sed -i 's/\r$//' contacts.vcf

```

---

### Post by benj1 on 2009-11-08
it should work but you could write it more simply as

```
awk 'BEGIN{FS=":"} /^EMAIL/{email = $2} /^FN/{print $2,email}'
```

---

### Post by WhiskyChris on 2009-11-08
You were right - running that sed command fixed the problems which had been annoying me for ages! The vcard file itself was generated from Evolution on ubuntu though so certainly didn't see windows anywhere, although I guess it must generate windows files...

Oh well, fixed now - thanks!

---

