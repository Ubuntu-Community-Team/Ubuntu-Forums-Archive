---
title: "Help with shell scripting please"
date: 2010-04-05
forum: General Help
---

### Post by karmic-koala on 2010-04-05
Hi!

I wrote a wee script that downloads a pdf file everyday. The PDF file is a newspaper's ecopy. I download it everyday. 

I use the wget command in the script to download the file. The name of the file changes everyday and I modify this before downloading.

The file name contains today's date which I am able to extract using date'+%d'. But how do I append the output of this to the wget command. 

E.g. url for today's date (05 April, 2010)
[http://www.xyz.com/download/05-04-10/epaper5-4-10.pdf](http://www.xyz.com/download/05-04-10/epaper5-4-10.pdf)

Is there a way to join the output of date to path string and supply this as url to wget?

---

### Post by ratcheer on 2010-04-05
[http://desk.stinkpot.org:8080/tricks/index.php/2007/02/concatenate-strings-in-bash/](http://desk.stinkpot.org:8080/tricks/index.php/2007/02/concatenate-strings-in-bash/)

Tim

---

### Post by mickObrian on 2010-04-05
dateOne=`date '+%d-%m-%g'`;
dateTwo=`date '+%-d-%-m-%g'`;
wget "http://www.xyz.com/download/$dateOne/epapers$dateTwo.pdf";

---

### Post by karmic-koala on 2010-04-06
Thanks guys for your input. Finally managed to get it right, the command that finally worked for me is

[COLOR="Red"]...
year=$(date +%G )
month=$(date +%-m )
day=$(date +%-d )

var="http://server.com/"${year}"_"${month}"_"$day".pdf"
wget $var

...[/COLOR]

---

