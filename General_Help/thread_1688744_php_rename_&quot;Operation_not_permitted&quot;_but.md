---
title: "php rename &quot;Operation not permitted&quot; but it worked?"
date: 2011-02-15
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2011-02-15
i used php to copy a file to the /tmp folder
```
copy("original.png","/tmp/original.png");
```process the image with convert command via shell_exec
move file back under a new name
```
rename("/tmp/original.png","original-edit-1.png");
```i tried to move it back after editing (under a new name)

i checked if the file exist right before i ran the rename function and it did
i checked after and it did not exist in the tmp folder
but it gave me an error message "Operation not permitted" however the operation was completed successfully
```
                        echo file_exists($tmpFile).'-before (tmp)<br/>';
                        echo file_exists($file).'-after (real)<br/>';
                        rename("$tmpFile",getcwd()."/$file");//access denied
                        //shell_exec("mv \"$tmpFile\" \"$file\"");
                        echo '<br/>'.file_exists($tmpFile).'-after (tmp)<br/>';
                        echo file_exists($file).'-after (real)<br/>';
```it gave me
```
1-before (tmp)
-after (real)
Warning:  rename(/tmp/original.png,/mnt/Public_HTML/scan/scans/original-edit-2.png):  Operation not permitted in /mnt/Public_HTML/scan/index.php on line 316 
-after (tmp)
1-after (real)
```


this gives me no errors
```
copy($tmpFile,$file);
unlink($tmpFile);
```

---

