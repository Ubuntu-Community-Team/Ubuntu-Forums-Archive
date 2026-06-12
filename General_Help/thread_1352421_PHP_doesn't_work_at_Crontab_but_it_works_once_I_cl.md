---
title: "PHP doesn't work at Crontab but it works once I click Run Now"
date: 2009-12-11
forum: General Help
---

### Post by aevny on 2009-12-11
[COLOR=#2446f0][FONT=Arial]This ‘bug’ drives me nuts all day long. I’m newbie in ubuntu.[/FONT][/COLOR]
 
[COLOR=#2446f0][FONT=Arial]Ubuntu 9.0.4[/FONT][/COLOR]
 
[COLOR=#2446f0][FONT=Arial]I have two php files which works great in website ( [http://abc/xx1.php](http://abc/xx1.php), http//abc/xx2/php ). I want to run on a regular basis.[/FONT][/COLOR]
 
[COLOR=#2446f0][FONT=Arial]So I installed php5-cli, and lynx both package.[/FONT][/COLOR]
 
[COLOR=#2446f0][FONT=Arial]Under Webmin - > System -> Schedule Cron Jobs, I like to have them to run in 2 minutes ( for testing purpose ). I have full permission to run these both reports as root user or permission granted user. [COLOR=darkred]It works great once I click ‘RUN NOW’ button on Webmin.[/COLOR][/FONT][/COLOR]
 
[COLOR=#2446f0][FONT=Arial]2 * * * * php /var/www/Tools/xx1.php >> /dev/null[/FONT][/COLOR]
 
[COLOR=#2446f0][FONT=Arial]However, I never get results after 2 or 20 minutes. Both reports can be run on web ( [http://abc/Toos/xx1.php](http://abc/Toos/xx1.php) ), or click ‘RUN NOW’ vai Webmin Cron Jobs. It really drive me to deep hole !:([/FONT][/COLOR]
 
[COLOR=#2446f0][FONT=Arial]Can someone help out ????? [/FONT][/COLOR]
 
[COLOR=#2446f0][FONT=Arial][COLOR=navy]**Thank you very much for your time and reply**[/COLOR].[/FONT][/COLOR]

---

