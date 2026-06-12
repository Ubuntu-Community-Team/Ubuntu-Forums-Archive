---
title: "Session suddenly terminate"
date: 2010-01-26
forum: General Help
---

### Post by viniciusandre on 2010-01-26
I don't know exaclty what's happening, but my session suddenly terminates and I go back to the login screen at random moments.

It happens quite often.
My syslog before the last time it happened:

Jan 26 09:39:01 parmesao CRON[14064]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Jan 26 10:09:01 parmesao CRON[15456]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Jan 26 10:14:29 parmesao pulseaudio[13079]: alsa-sink.c: O ALSA nos acordou para gravar novos dados no dispositivo, mas não há nada a ser gravado!
Jan 26 10:14:29 parmesao pulseaudio[13079]: alsa-sink.c: É mais provável que isso seja um erro no driver "snd_hda_intel" do ALSA. Por favor, relate esse problema para os desenvolvedores do ALSA.
Jan 26 10:14:29 parmesao pulseaudio[13079]: alsa-sink.c: Nós fomos acordados com o conjunto POLLOUT -- entretanto, a snd_pcm_avail() subseqüente retornou 0 ou outro valor < min_avail.
Jan 26 10:17:01 parmesao CRON[15825]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan 26 10:39:01 parmesao CRON[16732]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Jan 26 10:48:34 parmesao kernel: [10157.383699] hda-intel: Too big adjustment 32
Jan 26 10:52:58 parmesao gdm-simple-slave[17626]: WARNING: Unable to load file '/etc/gdm/custom.conf': Arquivo ou diretório não encontrado
Jan 26 10:52:58 parmesao acpid: client 12927[0:0] has disconnected
Jan 26 10:52:58 parmesao acpid: client 12927[0:0] has disconnected
Jan 26 10:52:58 parmesao acpid: client connected from 17628[0:0]
Jan 26 10:52:58 parmesao acpid: client connected from 17628[0:0]
Jan 26 10:53:03 parmesao bonobo-activation-server (vinicius-17700): could not associate with desktop session: Failed to connect to socket /tmp/dbus-5aD5vudbvi: Conexão recusada
Jan 26 10:53:05 parmesao pulseaudio[17782]: pid.c: Stale PID file, overwriting.
Jan 26 10:53:07 parmesao gnome-session[17734]: WARNING: Could not launch application 'nm-applet.desktop': Unable to start application: Falha ao executar processo filho "nm-applet" (Arquivo ou diretório não encontrado)
Jan 26 10:53:14 parmesao acpid: client 17628[0:0] has disconnected
Jan 26 10:53:14 parmesao acpid: client 17628[0:0] has disconnected
Jan 26 10:53:14 parmesao acpid: client connected from 17628[0:0]
Jan 26 10:53:14 parmesao acpid: client connected from 17628[0:0]

---

### Post by Jojochinoise on 2010-01-26
I'm having this issue as well. Can anyone look into it & see if there's any way to stop this from happening?

---

