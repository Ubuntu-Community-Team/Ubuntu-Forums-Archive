---
title: "Getting Links from Lynx"
date: 2010-09-03
forum: General Help
---

### Post by Guerreiro on 2010-09-03
Dear Esteemed Sirs and Madames,

I will get straight to the point, I am creating a small script to help me in my line of work, so far I got:


```
#!/bin/bash


echo "What site(s) do you want the data from?"
read URLList

echo "What filename do you want to give the saved file?"
read Filename

for URL in ${URLList}
do
{
host $URL | sed 's/http:\/\/$URL\//http:\/\/$URL/g' | grep address
echo "Total Domain"
lynx -source -accept_all_cookies "http://siteexplorer.search.yahoo.com/search?p=http://$URL&fr=sfp" | sed 's/</\
</g;s/>/>/g;s/<span\ class=\"btn\">//g'  | grep Pages
lynx -source -accept_all_cookies "http://siteexplorer.search.yahoo.com/search?p=http://$URL&fr=sfp&bwm=i" | sed 's/</\
</g;s/>/>/g;s/<li\ class=\"first\">Show\ Inlinks:/\ /g;s/<span\ class=\"btn\">//g'  | grep Inlinks

pr_checksum_prog="./pagerank"

if [ ! -x $pr_checksum_prog ]
then
 echo "Cannot Find Checksum Program: $pr_checksum_prog !"
 exit 2
fi

wget=/usr/bin/wget
prank_url=$URL
mod_prank_url=`echo $prank_url|sed -e 's/:/%3A/g' -e 's/\//%2F/g'`
prank_checksum=`$pr_checksum_prog $prank_url|sed 's/Checksum=//'`

prank_qurl="http://toolbarqueries.google.com/search?client=navclient-auto&ch=${prank_checksum}&ie=UTF-8&oe=UTF-8&features=Rank&q=info:${mod_prank_url}"

echo -n "Google PR For $prank_url = "

$wget -nv -O - "$prank_qurl" 2>&1|grep "Rank_"|sed 's/Rank_[0-9]:[0-9]://'

echo " "

} >> ./$Filename
done
```

Which with Pagerank command gotten from pagerank.c that I found on the web, will print the IP address, the indexed pages and the indexed links (from yahoo site explorer) and the current Pagerank. :) So now the last thing I need, is this;

The number of links on the page split into , Internal links (Linking to a Page on the same domain) and External links (linking to a page not on the same domain), and if it is possible how many are nofollow. :) Please help me out if you can. 

Best Regards.

PS. If you see a chance to clean up the code, that would be appreciated to of course!

---

