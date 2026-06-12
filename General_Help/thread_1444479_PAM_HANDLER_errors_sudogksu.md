---
title: "PAM_HANDLER errors sudo/gksu"
date: 2010-04-01
forum: General Help
---

### Post by bladerunner6 on 2010-04-01
I dont know if this is related to a recent update i done (last night?)

i get louds of pam_handlers.c messages when i try to run stuff as sudo or gksu, if i do a straight sudo su -, i got no errors as i am running root.

but as a normal use i get em. i cannot launch stuff like aptitude updates without errors, gparted, disk utility and so on.
i do gksu gparted in the terminal i get this message
[pam_handlers.c:_pam_parse_conf_file(286)] RETURN service_err(3) -> 0 ignore

i do sudo aptitude update i get these errors

[pam_handlers.c:_pam_parse_conf_file(286)] RETURN auth_err(7) -> -3 bad
[pam_handlers.c:_pam_parse_conf_file(286)] RETURN cred_insufficient( -> -3 bad
[pam_handlers.c:_pam_parse_conf_file(286)] RETURN authinfo_unavail(9) -> -3 bad
[pam_handlers.c:_pam_parse_conf_file(286)] RETURN user_unknown(10) -> -3 bad
[pam_handlers.c:_pam_parse_conf_file(286)] RETURN maxtries(11) -> -3 bad
[pam_handlers.c:_pam_parse_conf_file(286)] RETURN new_authtok_reqd(12) -> -1 ok
[pam_handlers.c:_pam_parse_conf_file(286)] RETURN acct_expired(13) -> -3 bad
[pam_handlers.c:_pam_parse_conf_file(286)] RETURN session_err(14) -> -3 bad
[pam_handlers.c:_pam_parse_conf_file(286)] RETURN cred_unavail(15) -> -3 bad
[pam_handlers.c:_pam_parse_conf_file(286)] RETURN cred_expired(16) -> -3 bad
[pam_handlers.c:_pam_parse_conf_file(286)] RETURN cred_err(17) -> -3 bad
[pam_handlers.c:_pam_parse_conf_file(286)] RETURN no_module_data(1 -> -3 bad
[pam_handlers.c:_pam_parse_conf_file(286)] RETURN conv_err(19) -> -3 bad
[pam_handlers.c:_pam_parse_conf_file(286)] RETURN authtok_err(20) -> -3 bad
[pam_handlers.c:_pam_parse_conf_file(286)] RETURN authtok_recover_err(21) -> -3 bad
[pam_handlers.c:_pam_parse_conf_file(286)] RETURN authtok_lock_busy(22) -> -3 bad
[pam_handlers.c:_pam_parse_conf_file(286)] RETURN authtok_disable_aging(23) -> -3 bad
[pam_handlers.c:_pam_parse_conf_file(286)] RETURN try_again(24) -> -3 bad
[pam_handlers.c:_pam_parse_conf_file(286)] RETURN ignore(25) -> 0 ignore
[pam_handlers.c:_pam_parse_conf_file(286)] RETURN abort(26) -> -3 bad
[pam_handlers.c:_pam_parse_conf_file(286)] RETURN authtok_expired(27) -> -3 bad
[pam_handlers.c:_pam_parse_conf_file(286)] RETURN module_unknown(2 -> -3 bad
[pam_handlers.c:_pam_parse_conf_file(286)] RETURN bad_item(29) -> -3 bad
[pam_handlers.c:_pam_parse_conf_file(286)] RETURN conv_again(30) -> -3 bad
[pam_handlers.c:_pam_parse_conf_file(286)] RETURN incomplete(31) -> -3 bad
[pam_handlers.c:_pam_add_handler(783)] called.
[pam_handlers.c:_pam_add_handler(797)] _pam_add_handler: adding type 2, handler_type 0, module `pam_unix.so'
[pam_handlers.c:_pam_load_module(655)] _pam_load_module: loading module `/lib/security/pam_unix.so'
[pam_handlers.c:_pam_add_handler(966)] _pam_add_handler: returning successfully
[pam_handlers.c:_pam_assemble_line(554)] called.
[pam_handlers.c:_pam_parse_conf_file(7] _pam_init_handler: LINE: session optional pam_winbind.so

[pam_handlers.c:_pam_parse_conf_file(101)] _pam_init_handlers: Found PAM config entry for: other
[pam_handlers.c:_pam_parse_conf_file(139)] Using config entry: session
[pam_handlers.c:_pam_parse_conf_file(175)] *PAM_F_OPTIONAL*
[pam_handlers.c:_pam_parse_conf_file(24] mod_path = pam_winbind.so
[pam_handlers.c:_pam_parse_conf_file(261)] list:

[pam_misc.c:_pam_mkargv(17] _pam_mkargv called:

[pam_misc.c:_pam_mkargv(19] [
]
[pam_misc.c:_pam_mkargv(219)] _pam_mkargv returned
[pam_handlers.c:_pam_parse_conf_file(263)] argvlen = 10
[pam_handlers.c:_pam_parse_conf_file(27] CONF: other(backup) 2 pam_winbind.so 0
[pam_handlers.c:_pam_parse_conf_file(286)] RETURN success(0) -> -1 ok
[pam_handlers.c:_pam_parse_conf_file(286)] RETURN open_err(1) -> 0 ignore
[pam_handlers.c:_pam_parse_conf_file(286)] RETURN symbol_err(2) -> 0 ignore
[pam_handlers.c:_pam_parse_conf_file(286)] RETURN service_err(3) -> 0 ignore
[pam_handlers.c:_pam_parse_conf_file(286)] RETURN system_err(4) -> 0 ignore
[pam_handlers.c:_pam_parse_conf_file(286)] RETURN buf_err(5) -> 0 ignore
[pam_handlers.c:_pam_parse_conf_file(286)] RETURN perm_denied(6) -> 0 ignore
[pam_handlers.c:_pam_parse_conf_file(286)] RETURN auth_err(7) -> 0 ignore
[pam_handlers.c:_pam_parse_conf_file(286)] RETURN cred_insufficient( -> 0 ignore
[pam_handlers.c:_pam_parse_conf_file(286)] RETURN authinfo_unavail(9) ->

and so on

---

### Post by bladerunner6 on 2010-04-01
anyone?

when i run passwd as root i get these issues also, somethings gone wrong with the system

---

### Post by bladerunner6 on 2010-04-02
i tracked down the issue to libpam modules from the 
[http://ppa.launchpad.net/gilir/lubuntu/ubuntu](http://ppa.launchpad.net/gilir/lubuntu/ubuntu) lucid ppa, cuasing these issues , downgrade  fixed em

---

