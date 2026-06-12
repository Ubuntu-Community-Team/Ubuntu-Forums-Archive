---
title: "How Can I Make This Script Better?"
date: 2011-01-23
forum: General Help
---

### Post by clockworkpc on 2011-01-23
The following script fetches all the comic strips that are available from the Bizarre Cathedral to date.
It is a very crude script:

1) I had to copy and paste the wget command 90 times
2) It won't fetch anything newer than comic strip #91
3) Every strip is called strip.jpg
4) The scripts saves each instance of strip.jpg into its own folder, i.e. /www.freesoftware.magazine.com/files/www.freesoftware.magazine.com/nodes/[4 digit number]/strip.jpg

How would you rewrite this script so that it does the following?

1) Fetch all of the comic strips with one line
2) Fetch everything from the very first to then newest
3) Save all the comic strips into one folder
4) Stamp each one with the number of the comic (e.g. 001 for the very first, 091 for the latest to date)
5) Exclude any strip that has already been downloaded

I'd really appreciate some pointers.

Thanks,

clockworkpc

THE SCRIPT:

#!/bin/bash

cd /media/DATA/Websites

wget -A "strip*" -r -l 3 [http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_1](http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_1)
wget -A "strip*" -r -l 3 [http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_2](http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_2)
wget -A "strip*" -r -l 3 [http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_3](http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_3)
wget -A "strip*" -r -l 3 [http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_4](http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_4)
wget -A "strip*" -r -l 3 [http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_5](http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_5)
wget -A "strip*" -r -l 3 [http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_6](http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_6)
wget -A "strip*" -r -l 3 [http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_7](http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_7)
wget -A "strip*" -r -l 3 [http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_8](http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_8)
wget -A "strip*" -r -l 3 [http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_9](http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_9)
wget -A "strip*" -r -l 3 [http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_10](http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_10)
wget -A "strip*" -r -l 3 [http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_11](http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_11)
wget -A "strip*" -r -l 3 [http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_12](http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_12)
wget -A "strip*" -r -l 3 [http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_13](http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_13)
wget -A "strip*" -r -l 3 [http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_14](http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_14)
wget -A "strip*" -r -l 3 [http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_15](http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_15)
wget -A "strip*" -r -l 3 [http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_16](http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_16)
wget -A "strip*" -r -l 3 [http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_17](http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_17)
wget -A "strip*" -r -l 3 [http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_18](http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_18)
wget -A "strip*" -r -l 3 [http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_19](http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_19)
wget -A "strip*" -r -l 3 [http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_20](http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_20)
wget -A "strip*" -r -l 3 [http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_21](http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_21)
wget -A "strip*" -r -l 3 [http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_22](http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_22)
wget -A "strip*" -r -l 3 [http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_23](http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_23)
wget -A "strip*" -r -l 3 [http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_24](http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_24)
wget -A "strip*" -r -l 3 [http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_25](http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_25)
wget -A "strip*" -r -l 3 [http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_26](http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_26)
wget -A "strip*" -r -l 3 [http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_27](http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_27)
wget -A "strip*" -r -l 3 [http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_28](http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_28)
wget -A "strip*" -r -l 3 [http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_29](http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_29)
wget -A "strip*" -r -l 3 [http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_30](http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_30)
wget -A "strip*" -r -l 3 [http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_31](http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_31)
wget -A "strip*" -r -l 3 [http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_32](http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_32)
wget -A "strip*" -r -l 3 [http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_33](http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_33)
wget -A "strip*" -r -l 3 [http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_34](http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_34)
wget -A "strip*" -r -l 3 [http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_35](http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_35)
wget -A "strip*" -r -l 3 [http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_36](http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_36)
wget -A "strip*" -r -l 3 [http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_37](http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_37)
wget -A "strip*" -r -l 3 [http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_38](http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_38)
wget -A "strip*" -r -l 3 [http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_39](http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_39)
wget -A "strip*" -r -l 3 [http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_40](http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_40)
wget -A "strip*" -r -l 3 [http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_41](http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_41)
wget -A "strip*" -r -l 3 [http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_42](http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_42)
wget -A "strip*" -r -l 3 [http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_43](http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_43)
wget -A "strip*" -r -l 3 [http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_44](http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_44)
wget -A "strip*" -r -l 3 [http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_45](http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_45)
wget -A "strip*" -r -l 3 [http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_46](http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_46)
wget -A "strip*" -r -l 3 [http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_47](http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_47)
wget -A "strip*" -r -l 3 [http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_48](http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_48)
wget -A "strip*" -r -l 3 [http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_49](http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_49)
wget -A "strip*" -r -l 3 [http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_50](http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_50)
wget -A "strip*" -r -l 3 [http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_51](http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_51)
wget -A "strip*" -r -l 3 [http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_52](http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_52)
wget -A "strip*" -r -l 3 [http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_53](http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_53)
wget -A "strip*" -r -l 3 [http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_54](http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_54)
wget -A "strip*" -r -l 3 [http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_55](http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_55)
wget -A "strip*" -r -l 3 [http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_56](http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_56)
wget -A "strip*" -r -l 3 [http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_57](http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_57)
wget -A "strip*" -r -l 3 [http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_58](http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_58)
wget -A "strip*" -r -l 3 [http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_59](http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_59)
wget -A "strip*" -r -l 3 [http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_60](http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_60)
wget -A "strip*" -r -l 3 [http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_61](http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_61)
wget -A "strip*" -r -l 3 [http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_62](http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_62)
wget -A "strip*" -r -l 3 [http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_63](http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_63)
wget -A "strip*" -r -l 3 [http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_64](http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_64)
wget -A "strip*" -r -l 3 [http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_65](http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_65)
wget -A "strip*" -r -l 3 [http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_66](http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_66)
wget -A "strip*" -r -l 3 [http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_67](http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_67)
wget -A "strip*" -r -l 3 [http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_68](http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_68)
wget -A "strip*" -r -l 3 [http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_69](http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_69)
wget -A "strip*" -r -l 3 [http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_70](http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_70)
wget -A "strip*" -r -l 3 [http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_71](http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_71)
wget -A "strip*" -r -l 3 [http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_72](http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_72)
wget -A "strip*" -r -l 3 [http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_73](http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_73)
wget -A "strip*" -r -l 3 [http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_74](http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_74)
wget -A "strip*" -r -l 3 [http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_75](http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_75)
wget -A "strip*" -r -l 3 [http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_76](http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_76)
wget -A "strip*" -r -l 3 [http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_77](http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_77)
wget -A "strip*" -r -l 3 [http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_78](http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_78)
wget -A "strip*" -r -l 3 [http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_79](http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_79)
wget -A "strip*" -r -l 3 [http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_80](http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_80)
wget -A "strip*" -r -l 3 [http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_81](http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_81)
wget -A "strip*" -r -l 3 [http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_82](http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_82)
wget -A "strip*" -r -l 3 [http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_83](http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_83)
wget -A "strip*" -r -l 3 [http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_84](http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_84)
wget -A "strip*" -r -l 3 [http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_85](http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_85)
wget -A "strip*" -r -l 3 [http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_86](http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_86)
wget -A "strip*" -r -l 3 [http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_87](http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_87)
wget -A "strip*" -r -l 3 [http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_88](http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_88)
wget -A "strip*" -r -l 3 [http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_89](http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_89)
wget -A "strip*" -r -l 3 [http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_90](http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_90)
wget -A "strip*" -r -l 3 [http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_91](http://www.freesoftwaremagazine.com/columns/bizarre_cathedral_91)

exit

---

