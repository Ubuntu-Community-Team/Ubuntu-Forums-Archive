---
title: "Installed Drupal from repositories, got lots of errors"
date: 2010-02-23
forum: General Help
---

### Post by Udibuntu on 2010-02-23
Hi All, please help, I got the following errors after trying to install Drupal6 from the repositories.

If this is not the right forum for this, please advise.

Thanks

> Warning: Table 'drupal6.access' doesn't exist query: SELECT 1 FROM access WHERE type = 'host' AND LOWER('127.0.0.1') LIKE LOWER(mask) AND status = 0 LIMIT 0, 1 in /usr/share/drupal6/includes/database.mysql.inc  on line 128

Warning: session_start() [function.session-start]: Cannot send session cookie - headers already sent by (output started at /usr/share/drupal6/includes/database.mysql.inc:128) in /usr/share/drupal6/includes/bootstrap.inc on line 1031

Warning: session_start() [function.session-start]: Cannot send session cache limiter - headers already sent (output started at /usr/share/drupal6/includes/database.mysql.inc:128) in /usr/share/drupal6/includes/bootstrap.inc on line 1031

Warning: Table 'drupal6.cache' doesn't exist query: SELECT data, created, headers, expire, serialized FROM cache WHERE cid = 'variables' in /usr/share/drupal6/includes/database.mysql.inc on line 128

Warning: Table 'drupal6.variable' doesn't exist query: SELECT * FROM variable in /usr/share/drupal6/includes/database.mysql.inc on line 128

Warning: Table 'drupal6.cache' doesn't exist query: UPDATE cache SET data = '', created = 1266946387, expire = 0, headers = '', serialized = 0 WHERE cid = 'variables' in /usr/share/drupal6/includes/database.mysql.inc on line 128

Warning: Table 'drupal6.system' doesn't exist query: SELECT name, filename, throttle FROM system WHERE type = 'module' AND status = 1 AND bootstrap = 1 ORDER BY weight ASC, filename ASC in /usr/share/drupal6/includes/database.mysql.inc on line 128

Warning: Cannot modify header information - headers already sent by (output started at /usr/share/drupal6/includes/database.mysql.inc:128) in /usr/share/drupal6/includes/bootstrap.inc on line 630

Warning: Cannot modify header information - headers already sent by (output started at /usr/share/drupal6/includes/database.mysql.inc:128) in /usr/share/drupal6/includes/bootstrap.inc on line 631

Warning: Cannot modify header information - headers already sent by (output started at /usr/share/drupal6/includes/database.mysql.inc:128) in /usr/share/drupal6/includes/bootstrap.inc on line 632

Warning: Cannot modify header information - headers already sent by (output started at /usr/share/drupal6/includes/database.mysql.inc:128) in /usr/share/drupal6/includes/bootstrap.inc on line 633

Warning: Table 'drupal6.url_alias' doesn't exist query: SELECT COUNT(pid) FROM url_alias in /usr/share/drupal6/includes/database.mysql.inc on line 128

---

### Post by Udibuntu on 2010-02-23
Used the right link to localhost, much ado about nothing...

---

