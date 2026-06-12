---
title: "file not uplading through apache"
date: 2009-08-26
forum: General Help
---

### Post by gbothma on 2009-08-26
HI there 

I have a brand new installation Ubuntu server 9.04 running Apache2, Mysql5, PHP5.

I have an old piece of code that was migraded from an old server which now does not work. 

I uploads a csv file which get processes and inserted into an MySQL DB.

I have no errors in Apache and syslogs

I have a sneaky suspision that it might have somehting to do with apparmor or alternativly permissions, but I'am not sure

import.html (snippet)

```
<form method="post" enctype="multipart/form-data" action="import.php">
    <table cellpadding="5" border="2">
    <tr>
        <td>File name to import</td>
        <td colspan="2"><input type="file" name="textfile" ></td>
    </tr>
    <tr>
      <td><input type="submit" value="Submit"></td>
    </tr>
    </table>
</form>
```

import.php (snippet)
```
<?php

include ('database.php');

define('STORE_PAGE_PARSE_TIME', 0);
define('STORE_PAGE_PARSE_TIME_LOG', 'parse_time_log');

define ('DB_SERVER', 'localhost');
define ('DB_SERVER_USERNAME', $username);
define ('DB_SERVER_PASSWORD', $password);
define ('DB_DATABASE', $dbase);
define ('USE_PCONNECT', 1);

  echo "<b><u> MySql catalog data import </u></b><br>";
  echo "<u> Results of import: </u>";

    $csvfile = fopen($textfile, "r")
        or die ("Unable to open the file: " . $textfile); <====[COLOR=Red][U]**I get this result**
[/U][/COLOR]
    tep_db_connect () or die ('Unable to connect to database');

```

Any assistance would be greatly appreciated

---

