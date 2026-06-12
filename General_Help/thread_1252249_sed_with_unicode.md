---
title: "sed with unicode"
date: 2009-08-28
forum: General Help
---

### Post by mdawg414 on 2009-08-28
There are a bunch of threads I have found regarding sed/grep with unicode files but every one basically boils down to converting the file to ascii before doing any operations. Unfortunately, that won't work for me and here's why.

I have a file encoded in unicode because there are some special characters (accents, foreign characters, etc) but each line contains a URL. The URL has no unicode characters in it but it is still encoded that way. I need to do a mass replace on these URLs and I have already written that script to work on an ascii file. However, if I convert the list to ascii first, then use sed to replace the URLs, the unicode characters are not the same anymore. This is a problem because when I import the file into the program I am using (it happens to be Google AdWords Editor if that helps anyone), it creates new entries rather than updating the old ones since the other fields are not the same any more. 

So basically, here is what I need: I need to replace ascii URLs, encoded in unicode, but preserve the characters of the rest of the line. The ideal approach would be to have sed or grep work on unicode but that doesn't seem to work. Any ideas? I understand this might not make sense so don't hesitate to ask for more clarification.

Thanks a lot!

---

### Post by DaithiF on 2009-08-28
sounds like you need a sed-replacement that supports unicode.  maybe a python script.  can you post a short sample of the file and the sed-script you wrote?

---

### Post by mdawg414 on 2009-08-28
I have attached two 3-line snippets of the file in question. One (titled unicode_file) is encoded in unicode and the other (titled ascii_file) is encoded in ascii via the following iconv command:
```

iconv -f unicode -t ascii//TRANSLIT unicode_file.txt > ascii_file.txt

```

For simplicity, let's just try to replace the domain hotelreservations.com in the URLs with mydomain.com. So the following sed script would work on the ascii file
```

sed -e 's#hotelreservations.com#mydomain.com#i' ascii_file.txt

```

So ideally, the foreign characters would still be there in unicode but the domains would be switched. 

Thanks again.

P.S:
Any idea where I could find such a python script?

---

### Post by DaithiF on 2009-08-29
Hi,
something like:
```
fh = open('unicode_file.txt')
raw = fh.read()
fh.close()

raw = raw[1:-1]         # corrupted file? (bad 1st & last byte chars)

u = raw.decode('utf16')

replace_patterns = [ ('HotelReservations.com', 'mydomain.com'),
                    ( 'nextreplacefrom', 'nextreplaceto') ]

print "Before: %s" % u

for x,y in replace_patterns:
    u = u.replace(x, y)

print "After: %s" % u
```

gives:
```
Before: CityA   163076 Le Méridien Apollo Hotel - Amsterdam     Apollo Amsterdam
        Broad   0.22    0.07    7       http://Book.HotelReservations.com/hotel/propertydetails/163076/?currencyCode=USD&locale=en_US&cid=165272&utm_source=adwords&utm_medium=plm&utm_campaign=CityA&utm_extra=DIM1/163076+Le+M%E9ridien+Apollo+Hotel+-+Amsterdam//DIM2/Broad&utm_term=Apollo+Amsterdam        Active  Active Active
CityA   163076 Le Méridien Apollo Hotel - Amsterdam     Apollo Amsterdam Netherlands    Broad   0.36    0.40    4       http://Book.HotelReservations.com/hotel/propertydetails/163076/?currencyCode=USD&locale=en_US&cid=165272&utm_source=adwords&utm_medium=plm&utm_campaign=CityA&utm_extra=DIM1/163076+Le+M%E9ridien+Apollo+Hotel+-+Amsterdam//DIM2/Broad&utm_term=Apollo+Amsterdam+Netherlands    Active Active   Active
CityA   163076 Le Méridien Apollo Hotel - Amsterdam     Apollo Amsterdam Netherlands Europe     Broad   0.40    1.00    3       http://Book.HotelReservations.com/hotel/propertydetails/163076/?currencyCode=USD&locale=en_US&cid=165272&utm_source=adwords&utm_medium=plm&utm_campaign=CityA&utm_extra=DIM1/163076+Le+M%E9ridien+Apollo+Hotel+-+Amsterdam//DIM2/Broad&utm_term=Apollo+Amsterdam+Netherlands+Europe     Active  Active  Active
After: CityA    163076 Le Méridien Apollo Hotel - Amsterdam     Apollo Amsterdam
        Broad   0.22    0.07    7       http://Book.mydomain.com/hotel/propertydetails/163076/?currencyCode=USD&locale=en_US&cid=165272&utm_source=adwords&utm_medium=plm&utm_campaign=CityA&utm_extra=DIM1/163076+Le+M%E9ridien+Apollo+Hotel+-+Amsterdam//DIM2/Broad&utm_term=Apollo+Amsterdam Active  Active  Active
CityA   163076 Le Méridien Apollo Hotel - Amsterdam     Apollo Amsterdam Netherlands    Broad   0.36    0.40    4       http://Book.mydomain.com/hotel/propertydetails/163076/?currencyCode=USD&locale=en_US&cid=165272&utm_source=adwords&utm_medium=plm&utm_campaign=CityA&utm_extra=DIM1/163076+Le+M%E9ridien+Apollo+Hotel+-+Amsterdam//DIM2/Broad&utm_term=Apollo+Amsterdam+Netherlands     Active  Active Active
CityA   163076 Le Méridien Apollo Hotel - Amsterdam     Apollo Amsterdam Netherlands Europe     Broad   0.40    1.00    3       http://Book.mydomain.com/hotel/propertydetails/163076/?currencyCode=USD&locale=en_US&cid=165272&utm_source=adwords&utm_medium=plm&utm_campaign=CityA&utm_extra=DIM1/163076+Le+M%E9ridien+Apollo+Hotel+-+Amsterdam//DIM2/Broad&utm_term=Apollo+Amsterdam+Netherlands+Europe     Active   Active  Active

```
note that I had a problem decoding the unicode file as provided, I had to strip off the first & last chars before I could decode it into meaningful text.

---

