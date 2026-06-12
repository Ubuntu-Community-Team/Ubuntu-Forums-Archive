---
title: "Bash Scrpting Help"
date: 2010-01-26
forum: General Help
---

### Post by joshpennington on 2010-01-26
Hello-

I am trying to run a PHP script over and over again.  I would love to be able to just write a small bash script that will just do this for me, however I am having trouble writing a for loop that works.  Here is what I have now:

#! /bin/bash
for i in {1..20} do
  php wps_product_import.php
done

When I run this (./bash_import) I get the following errors:

./bash_import: line 3: syntax error near unexpected token `php'
./bash_import: line 3: `  php wps_product_import.php'

I have also tried just doing the "php wps_product_import.php" on 20 different lines and I get an error saying it can't open the script file and only runs once.

Any help would be very much appreciated.

Josh Pennington

---

### Post by t4thfavor on 2010-01-26
> **joshpennington said:**
> Hello-

I am trying to run a PHP script over and over again.  I would love to be able to just write a small bash script that will just do this for me, however I am having trouble writing a for loop that works.  Here is what I have now:

#! /bin/bash
for i in {1..20} do
  php wps_product_import.php
done

When I run this (./bash_import) I get the following errors:

./bash_import: line 3: syntax error near unexpected token `php'
./bash_import: line 3: `  php wps_product_import.php'

I have also tried just doing the "php wps_product_import.php" on 20 different lines and I get an error saying it can't open the script file and only runs once.

Any help would be very much appreciated.

Josh Pennington


Try 

```

#! /bin/bash
for i in {1..20} do
  `php /path/to/wps_product_import.php`
done

```
Add the greives or backticks to the command, they should be on the key with the tilde.~~~

---

### Post by Agent ME on 2010-01-26
That won't work.

You use backticks when you want to insert the output of a program onto the command line of the command to run. There also probably shouldn't be a space on the first line, but I don't know if that's fatal.

The main problem was that in the original script, "do" was on the same line as "for". You have to put a semicolon between them or put them on separate lines.
```
#!/bin/bash
for i in {1..20}
do
  php /path/to/wps_product_import.php
done
```

---

### Post by joshpennington on 2010-01-26
Thank you for your help!

I tried your code and this is what I came up with:


#! /bin/bash
for i in {1..20} do
  `php /var/www/magento_import/wps_product_import.php`
done

I got the following error:

./bash_import: line 3: syntax error near unexpected token ``php /var/www/magento_import/wps_product_import.php`'

./bash_import: line 3: `  `php /var/www/magento_import/wps_product_import.php`'

Do you have any other ideas?

Thanks again.

---

### Post by t4thfavor on 2010-01-26
Oops, your right, I was thinking of something else I guess.

I got the same error when trying to run your script, turns out I had forgotten to install php on my laptop. Make sure it's installes as the same script runs without error on my server.

---

### Post by lavinog on 2010-01-26
nm

---

### Post by joshpennington on 2010-01-26
This is getting weird.  I am getting the same error so I guess maybe I should consider the way I am working on the server to see if that makes a difference.

I am accessing the server over SSH using Putty.  I used joe to create the file.  The file permissions have been set to 777.

I am able to run the php script without error by typing in (so I know the script works):

php /var/www/magento_import/wps_product_import.php

Are there any sensitivities for line breaks or something weird like that that could be effecting me?

Thanks

---

### Post by t4thfavor on 2010-01-26
It runs because I inadvertently fixed the loop, you are missing a semicolon after the }, and one after the php line. Sorry, I was working in automatic mode I guess.

```

#! /bin/bash
for i in {1..20}; do
        php /home/chance/test.php;
done

```

---

### Post by lavinog on 2010-01-26
> **joshpennington said:**
> This is getting weird.  I am getting the same error so I guess maybe I should consider the way I am working on the server to see if that makes a difference.

I am accessing the server over SSH using Putty.  I used joe to create the file.  The file permissions have been set to 777.

I am able to run the php script without error by typing in (so I know the script works):

php /var/www/magento_import/wps_product_import.php

Are there any sensitivities for line breaks or something weird like that that could be effecting me?

Thanks
what about this:
```

for x in {1..20};do php /var/www/magento_import/wps_product_import.php;done


```

---

### Post by joshpennington on 2010-01-26
Adding the ; has made it work exactly the way I was hoping.  

Thanks much all!  You have saved me a lot of time from having to press up and enter like 5000 times

---

