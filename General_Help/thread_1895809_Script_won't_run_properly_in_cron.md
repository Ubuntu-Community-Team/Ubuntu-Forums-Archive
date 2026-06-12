---
title: "Script won't run properly in cron"
date: 2011-12-15
forum: General Help
---

### Post by Westerberg on 2011-12-15
I'm don't understand why this script runs flawlessly from the command line but runs incompletely from cron.

This script is supposed to download some html files from a web host and check to see whether they contain a line.  If they don't contain the line, they get moved to another folder where line is added.  Finally, the edited files get uploaded to the host.

Here's my script:

```

#!/bin/bash -x

home_dir="/home/james/Desktop/upload_apenterprisesllc"
DOCTYPE='<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN">'
loose=' "http://www.w3.org/TR/html4/loose.dtd">'

failure_test () {

	if [ $? -ne 0 ]; then

		failure_alert "$1" "$2"

		exit 1

	fi

}


failure_alert () {

	echo "$1" | mutt -s "$2" ***********@verizon.net

}


lftp -u *********@aol.com,goforbroke ftp.intuitwebsites.com <<EOD
set net:timeout 50
cd apenterprises || quit 1
mget -c -O $home_dir/ *html || quit 1
quit 0
EOD

failure_test "Couldn't download html files" "$0 error"

sleep 5

for i in $home_dir/*html; do

	head $i | grep http://www.w3.org/TR/html4/loose.dtd &>/dev/null || mv $i "$home_dir/to_be_uploaded/"


done

if ls /home/james/Desktop/upload_apenterprisesllc/to_be_uploaded/*html &>/dev/null; then

	for j in "${home_dir}/to_be_uploaded/*html"; do

		awk -v DOCTYPE="$DOCTYPE" -v loose="$loose" '/DOCTYPE/{sub(/>/,loose)}{print}' $j \
		> ${home_dir}/to_be_uploaded/temp && rm $j && mv ${home_dir}/to_be_uploaded/temp ${home_dir}/to_be_uploaded/`basename "$j"` \
		|| failure_alert "Could not edit html files" "$0 failure" 


	done

	lftp -u *********@aol.com,goforbroke ftp.intuitwebsites.com <<EOD
set net:timeout 50
mput -c -O /apenterprises ${home_dir}/to_be_uploaded/*html || quit 1
quit 0
EOD

	failure_test "Couldn't upload html files" "$0 error"

	rm ${home_dir}/*html

	failure_test "Couldn't delete html files" "$0 error"

	rm ${home_dir}/to_be_uploaded/*html

	failure_test "Couldn't delete html files" "$0 error"

	exit 0

else

  rm ${home_dir}/*html

  failure_test "Couldn't delete html files" "$0 error"

	exit 0

fi
```

Here's the error output when the script is run in cron:
> awk: cmd. line:1: fatal: cannot open file `/home/james/Desktop/upload_apenterprisesllc/to_be_uploaded/*html' for reading (No such file or directory)
ls: cannot access /home/james/Desktop/upload_apenterprisesllc/to_be_uploaded/*html: No such file or directory
mput: /home/james/Desktop/upload_apenterprisesllc/to_be_uploaded/*html: no files found

The problem seems to be cron doesn't recognize my flow control.  If there are no html files in the "to_be_uploaded" file, it's supposed to skip the awk-ing and uploading to the server section.  But it doesn't for some reason and it tries to edit and upload files that don't exist.

Here's my crontab: 
> 0 * * * * /home/james/bin/upload_apenterprisesllc.bs 2>/home/james/failure.txt

Any idea ?  I'm stumped.

---

### Post by Westerberg on 2011-12-15
I figured it out.
Cron has its own environmental variables, some of which are different from bash terminal's.
For a shell, Cron uses /bin/sh while the terminal uses /bin/bash.
Also, Cron's PATH variable may be different from the bash terminal's.

So I added to my crontab
```
SHELL=/bin/bash
PATH=/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
```

Doing this seems to have solved the problem.

---

