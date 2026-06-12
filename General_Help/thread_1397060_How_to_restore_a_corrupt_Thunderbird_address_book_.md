---
title: "How to restore a corrupt Thunderbird address book using PHP"
date: 2010-02-02
forum: General Help
---

### Post by mikerobinson on 2010-02-02
My address book recently got corrupted and I was unable to restore the e-mails, however looking at my abook.mab file I could see that all of the e-mail addresses were in there. I wrote a php script to create a new tab delimited text file, which you can import into Thunderbird. I used it to recover about 7300 contacts and it seems to work well for the most part. Just change 'abook.mab' to point to your actual corrupt abook.mab file or put it in the same directory as the script.

[PHP]<?php
error_reporting(E_ALL);
$abook = file_get_contents('abook.mab');

preg_match_all('/\((.*)\)/Ums', $abook, $matches);

$matches = $matches[1];


foreach ($matches as $key => $match) {
	$entry = explode('=', $match);
	if (isset($entry[1]) && strlen($entry[1]) > 4 && !isset($skipnext)) {
		$entry[1] = str_replace("\\\n", '', $entry[1]);
		$entry[1] = str_replace('\\\\', '', $entry[1]);
		$entry[1] = str_replace('\\', ')', $entry[1]); // the backslashes SHOULD be at the end of each line
		
		// Unicode characters
		if (strstr($entry[1],'$')) {
			$entry[1] = str_replace('$', "\\x", $entry[1]);
			$entry[1] = preg_replace("#(\\\x[0-9A-F]{2})#e", "chr(hexdec('\\1'))", $entry[1]);
		}

		
		$matches[$key] = utf8_decode($entry[1]);
		if (strstr($entry[1],'@')) $skipnext = true;
	}
	else {
		unset($matches[$key]);
		unset($skipnext);
		if (strstr($entry[1],'@')) $skipnext = true;
	}
	unset($entry);
}

$previous = null;
foreach ($matches as $match) {
	if (strstr($match,'@')) {
		if (strtolower($match) != strtolower($previous)) {
			if (isset($addy)) $addressbook[] = array($match, end($addy));
			else $addressbook[] = array($match, $match);
			unset($addy);
			$previous = $match;
		}
	}
	else {
		$addy[] = $match;
	}
}

echo "First Name\tLast Name\tDisplay Name\tNickname\tPrimary Email\tSecondary Email\tScreen Name\tWork Phone\tHome Phone\tFax Number\tPager Number\tMobile Number\tHome Address\tHome Address 2\tHome City\tHome State\tHome ZipCode\tHome Country\tWork Address\tWork Address 2\tWork City\tWork State\tWork ZipCode\tWork Country\tJob Title\tDepartment\tOrganization\tWeb Page 1\tWeb Page 2\tBirth Year\tBirth Month\tBirth Day\tCustom 1\tCustom 2\tCustom 3\tCustom 4\tNotes\t";
foreach ($addressbook as $addy) {
	echo "\t\t{$addy[1]}\t\t{$addy[0]}\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t\n";
}[/PHP]

Feel free to use it to recover your address book files if you can't do it manually.

---

### Post by t4thfavor on 2010-02-02
Mark this solved.

It looks like a very useful script.

---

### Post by TobalJackson on 2012-03-14
Hello Mikerobinson, thank you for this php code, it looks like it has worked for some, but I'm having trouble getting it to work properly.  When I run the code ```
php savior.php > book.txt
``` I get the error ```
PHP Notice: Undefined offset: 1 in /savior.php on line 28
```

looking at line 28 of the code, it looks like ```
if (strstr($entry[1],'@')) $skipnext = true;
``` is the offending piece of code.  Googling told me that this error means that $entry[1] is undefined when it reaches this line, but I don't know enough about PHP to correct this.  

Please let me know if you have any suggestions as I'm trying to recover several thousand contacts from corrupted thunderbird abook.mab.  Thanks again.

---

### Post by mikerobinson on 2012-03-15
You could try changing it to this:

```
if (isset($entry[1]) && strstr($entry[1],'@')) $skipnext = true;
```

---

### Post by gcc on 2013-03-04
Thanks Mike Robinson for this!

It restored some data for me, but I wanted to go further, so I wrote this code:

[https://github.com/qris/thunderbird-ldif](https://github.com/qris/thunderbird-ldif)

I hope it's useful to someone.

---

