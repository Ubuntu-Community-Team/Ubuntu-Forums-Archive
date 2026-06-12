---
title: "File Transfer using samba help."
date: 2010-08-03
forum: General Help
---

### Post by mcclunyboy on 2010-08-03
Right,

Might have been better under development/programming but I don't consider myself a programmer so didnt post there.

Right I want to move multiple files from 1 server to another (windows to Linux) using SMBCLIENT as FTP is disabled.  For some reason this is failing, see below:

My problem is that the files don't seem to be recognised.  It always  quotes the file names as thisfile* when in reality they should be  thisfile12072010 or thisfile13072010, using * as the wildcard.  I have tested using a slightly different scipt and it worked fine.


```

smbclient //server/share password -U user >> $LOGGING<< EOF
cd $EXTERNALDIRECTORY
prompt
mget $EXTERNALFILE1
exit
EOF

echo " Files pulled - checking delivery " | tee -a $LOGGING

for file in thesefiles*
do
    echo "Checking file size of $file"
    if [ -s "$ChequeFile" ]
    then
    echo "File "$file" is suitable for processing."
    else
    echo "Error -File "$file" appears to have been transferred with zero bytes"
    exit 1
    fi
echo "FTP Transfer ended Successfully" | tee -a $LOGGING
echo "
echo "File "$file"
echo " Transferred from remote File Server"
echo "    "
done 

```

ANy thoughts?

---

### Post by pricetech on 2010-08-03
Have you tried copying one or more files manually to see if Samba and your network are up to the task ??

Have you tried any other means besides Samba to access the files ??

---

