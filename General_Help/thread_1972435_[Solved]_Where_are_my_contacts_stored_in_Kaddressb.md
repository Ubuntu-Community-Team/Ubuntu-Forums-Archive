---
title: "[Solved] Where are my contacts stored in Kaddressbook/Kontact?"
date: 2012-05-03
forum: General Help
---

### Post by myrddinemrys on 2012-05-03
Last week I did a clean install of Kubuntu 12.04 after carefully backing up my previous home folder of my previous install (11.04).  I always note where all my previous settings are so I can move them over to the new install.  Everything worked great until I went to transfer my contacts from where I had noted they were, **.kde/share/apps/kabc/std.vcf**.  Nope, not there.  I know [this]("http://userbase.kde.org/KMail/FAQs_Hints_and_Tips#Transfer_mail_and_settings_to_another_computer_.28or_another_user_account_on_the_same_machine.29") says they're stored there, but they weren't.  Most of my searches told me they would be there or in **.local/share/contacts**, but that path didn't even exist for me.

After a great deal of searching, my ultimate solution was located [here]("http://www.guyrutenberg.com/2011/08/28/extracting-data-from-akonadi-kontact/"), and even then it didn't work on Kubuntu without some changes.

Apparently, at least for the version of Kontact in Kubuntu 11.04 (4.4.10), the contacts (even though the KDE settings say they're located in the "kabc" folder) are actually embedded in the binary file **ibdata1** located in the **.local/share/akonadi/db_data** folder.  Using the following script can pull out your contacts and calendar items from this file. It is a modification of the script used in the above link, so it will work in Kubuntu.

```
#!/usr/bin/python
import sys

# Usage: Copy this file into the Akonadi database folder,
# (~/.local/share/akonadi/db_data), then run like this:
#
# ./exportinfo.py > contacts.vcf
#
# This means, run this python script on file "ibdata1" and
# output the results into file "contacts.vcf"

#START_DELIM = "BEGIN:VCALENDAR"
#END_DELIM = "END:VCALENDAR"
START_DELIM = "BEGIN:VCARD"
END_DELIM = "END:VCARD"
def main():
    #bin_data = sys.stdin.read()
    file1 = open("ibdata1","rb")
    bin_data = file1.read()
    
    vcards = []
 
    start = bin_data.find(START_DELIM)
    while start > -1:
        end = bin_data.find(END_DELIM,start+1)
        vcards.append(bin_data[start:end + len(END_DELIM)])
        start = bin_data.find(START_DELIM, end+1)
 
    print "\n".join(vcards)
 
 
 
if __name__=="__main__":
    main()


```

What I did was save the code above (the file is attached too) into the **~/.local/share/akonadi/db_data** folder as "exportinfo.py" and set it as executable:

```
chmod a+x exportinfo.py
```

THen run it with this command to export the addresses into a VCard file that can be imported into KAddressbook/Kontact:

```
./exportinfo.py > contacts.vcf
```

Hope this helps someone.  I'm no python expert so please no harsh criticisms of the script.  It worked, and that's what mattered to me.

---

