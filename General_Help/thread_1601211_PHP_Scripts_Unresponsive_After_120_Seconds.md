---
title: "PHP Scripts Unresponsive After 120 Seconds"
date: 2010-10-19
forum: General Help
---

### Post by danovotny on 2010-10-19
This one really has me stumped. I have not ran across this problem on any other servers I have worked on.

This is on an Ubuntu 10.04.1 LTS server with PHP 5.3.2-1ubuntu4.5.

When I have a PHP script that does not have any output for over 120 seconds, the script will not show any subsequent output; however, any non-output will still be executed. This happens for both php5-cgi & php5 (cli). For example:

[PHP]1. $iSleep = 120;
2. echo 'Now: '.date('H:i:s')."\n";
3. echo 'Sleeping for: '.$iSleep."\n";
4. echo 'Will wake up at: '.date('H:i:s', (time()+$iSleep))."\n";
5. sleep($iSleep);
6. echo 'Woke up at: '.date('H:i:s')."\n";
7. mail('test@example.com', 'Subject', 'Message');[/PHP]

I will get all the output back to the screen through line 4. Line 6 will never appear on the screen, but I will get an email from line 7. If I change line 1 to be 119 or less, the code will execute fully as expected.

I have changed max_execution_time = 0 in the php.ini and have used set_time_limit(0); but neither have solved the problem.

Please let me know if there are any other settings (php.ini) or version numbers that you want to know. Thanks in advance for your time.

-------------------------------------

A few days later this problem no longer presents itself. Sorry for the trouble.

---

