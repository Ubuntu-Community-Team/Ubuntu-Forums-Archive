---
title: "Narrow display"
date: 2011-12-20
forum: General Help
---

### Post by Nemo103 on 2011-12-20
I installed Milkytracker yesterday, and was changing the programme's resolution. My display now takes up the central half or so of my monitor, instead of all of it. It's only the case when I'm logged in as me. Removing Milkytracker didn't fix it. Changing the resolution of the display in Monitors doesn't affect it.

Any thoughts? Thanks.


EDIT

I don't know how, but it fixed itself. I closed the lid on my laptop, and came back to normal screen. (Rebooting hadn't fixed it before...)

---

### Post by Nemo103 on 2011-12-20
Not quite solved: after logging in, the problem persists, but if I close the lid and open again it returns to normal

---

### Post by Nemo103 on 2011-12-20
Now it refuses to shut down normally. Some error about a plymouth command comes up.

I've ["debugged plymouth"]("https://wiki.ubuntu.com/Plymouth#Enabling_Logging"), but I've no idea what the resulting log file means. Here it is:

> [main.c]                                 check_logging:checking if console messages should be redirected and logged
[main.c]                                 check_logging:logging will be enabled!
[main.c]                            check_for_consoles:checking for consoles
[main.c]                            check_for_consoles:There are currently 0 text displays
[main.c]                redirect_standard_io_to_device:redirecting stdio to /dev/tty7
[main.c]                        initialize_environment:initialized minimal work environment
[main.c]                     attach_to_running_session:creating new terminal session
[ply-terminal-session.c]                   ply_terminal_session_attach:ptmx not passed in, creating one
[ply-terminal-session.c]                           open_pseudoterminal:opening device '/dev/ptmx'
[ply-terminal-session.c]                           open_pseudoterminal: opened device '/dev/ptmx'
[ply-terminal-session.c]                           open_pseudoterminal:creating pseudoterminal
[ply-terminal-session.c]                           open_pseudoterminal:done creating pseudoterminal
[ply-terminal-session.c]                           open_pseudoterminal:unlocking pseudoterminal
[ply-terminal-session.c]                           open_pseudoterminal:unlocked pseudoterminal
[ply-terminal-session.c]                   ply_terminal_session_attach:redirecting system console to terminal device
[ply-terminal-session.c]                   ply_terminal_session_attach:done redirecting system console to terminal device
[main.c]                       get_cache_file_for_mode:returning cache file '/var/lib/plymouth//boot-duration'
[main.c]                                          main:entering event loop
[ply-boot-server.c]                ply_boot_connection_on_request:got show splash request
[main.c]      plymouth_should_ignore_show_splash_calls:checking if plymouth should be running
[main.c]                            check_for_consoles:checking for consoles and adding displays
[main.c]                            check_for_consoles:There are currently 0 text displays
[main.c]             add_default_displays_and_keyboard:adding default displays and keyboard
[ply-utils.c]                               ply_open_module:Could not load module "/lib/plymouth/renderers/x11.so": /lib/plymouth/renderers/x11.so: cannot open shared object file: No such file or directory

[./plugin.c]                                create_backend:creating renderer backend for device /dev/dri/card0
[./plugin.c]                                   load_driver:Attempting to load driver 'i915'
[ply-terminal.c]                             ply_terminal_open:trying to open terminal '/dev/tty7'
[ply-terminal.c]                 ply_terminal_look_up_geometry:looking up terminal text geometry
[ply-terminal.c]                 ply_terminal_look_up_geometry:terminal is now 170x48 text cells
[./plugin.c]                         ply_renderer_head_new:Creating 1366x768 renderer head
[main.c]                                  set_keyboard:listening for keystrokes
[main.c]                                  set_keyboard:listening for backspace
[main.c]                                  set_keyboard:listening for enter
[main.c]              add_pixel_displays_from_renderer:Adding displays for 1 heads
[main.c]           plymouth_should_show_default_splash:checking if plymouth should show default splash
[main.c]                           show_default_splash:Showing splash screen
[main.c]                    find_system_default_splash:Trying to load /etc/plymouth//plymouthd.conf
[ply-key-file.c]                        ply_key_file_open_file:Failed to open key file /etc/plymouth//plymouthd.conf: No such file or directory
[main.c]                    find_system_default_splash:failed to load /etc/plymouth//plymouthd.conf
[main.c]              find_distribution_default_splash:Trying to load /lib/plymouth//plymouthd.defaults
[ply-key-file.c]                        ply_key_file_open_file:Failed to open key file /lib/plymouth//plymouthd.defaults: No such file or directory
[main.c]              find_distribution_default_splash:failed to load /lib/plymouth//plymouthd.defaults
[main.c]                           show_default_splash:Trying old scheme for default splash
[main.c]                             start_boot_splash:Loading boot splash theme '/lib/plymouth/themes/default.plymouth'
[ply-key-file.c]                       ply_key_file_load_group:trying to load group Plymouth Theme
[ply-key-file.c]                       ply_key_file_load_group:trying to load group script
[ply-key-file.c]                      ply_key_file_load_groups:key file has no more groups
[main.c]                             start_boot_splash:attaching plugin to event loop
[main.c]                             start_boot_splash:attaching progress to plugin
[main.c]      add_displays_and_keyboard_to_boot_splash:setting keyboard on boot splash
[main.c]      add_displays_and_keyboard_to_boot_splash:adding pixel display on boot splash
[main.c]      add_displays_and_keyboard_to_boot_splash:adding text display on boot splash
[main.c]                             start_boot_splash:showing plugin
[ply-boot-splash.c]                          ply_boot_splash_show:showing splash screen

[./plugin.c]                            show_splash_screen:starting boot animation
[./plugin.c]                               start_animation:parsing script file
[./plugin.c]                        start_script_animation:executing script file
[ply-label.c]                                ply_label_free:Unloading label control plugin
[ply-label.c]                                ply_label_free:Unloading label control plugin
[ply-label.c]                                ply_label_free:Unloading label control plugin
[ply-label.c]                                ply_label_free:Unloading label control plugin
[./plugin.c]                         ply_renderer_head_map:Creating buffer for 1366x768 renderer head
[./ply-renderer-i915-driver.c]                       ply_renderer_buffer_new:returning 1366x768 buffer with stride 5632
[./plugin.c]                         ply_renderer_head_map:Mapping buffer for 1366x768 renderer head
[./plugin.c]                      ply_renderer_head_redraw:Redrawing 1366x768 renderer head
[./plugin.c]                         ply_renderer_head_map:Setting scan out buffer of 1366x768 head to our buffer
[./plugin.c]                                      activate:taking master and scanning out
[ply-event-loop.c]              ply_event_loop_disconnect_source:disconnecting source with fd 7
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:calling disconnected_handler 0x804d190 for fd 7
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:done calling disconnected_handler 0x804d190 for fd 7
[ply-event-loop.c]              ply_event_loop_disconnect_source:done disconnecting source with fd 7
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing watches for source with fd 7
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing watches for source with fd 7
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing destinations for source with fd 7
[ply-event-loop.c]   ply_event_loop_free_destinations_for_source:freeing destination (1, 0x804bc20, 0x804d190) of fd 7
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing destinations for source with fd 7
[ply-event-loop.c]              ply_event_loop_disconnect_source:removing source with fd 7 from event loop
[ply-event-loop.c]              ply_event_loop_disconnect_source:done removing source with fd 7 from event loop
[ply-boot-server.c]                ply_boot_connection_on_request:got newroot request
[main.c]                                    on_newroot:new root mounted at "/root", switching to it
[ply-event-loop.c]              ply_event_loop_disconnect_source:disconnecting source with fd 7
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:calling disconnected_handler 0x804d190 for fd 7
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:done calling disconnected_handler 0x804d190 for fd 7
[ply-event-loop.c]              ply_event_loop_disconnect_source:done disconnecting source with fd 7
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing watches for source with fd 7
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing watches for source with fd 7
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing destinations for source with fd 7
[ply-event-loop.c]   ply_event_loop_free_destinations_for_source:freeing destination (1, 0x804bc20, 0x804d190) of fd 7
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing destinations for source with fd 7
[ply-event-loop.c]              ply_event_loop_disconnect_source:removing source with fd 7 from event loop
[ply-event-loop.c]              ply_event_loop_disconnect_source:done removing source with fd 7 from event loop
[ply-boot-server.c]                ply_boot_connection_on_request:got system initialized notification
[main.c]                         on_system_initialized:system now initialized, opening log
[main.c]                         get_log_file_for_mode:returning log file '/var/log/boot.log'
[main.c]                               prepare_logging:opening log '/var/log/boot.log'
[ply-event-loop.c]              ply_event_loop_disconnect_source:disconnecting source with fd 11
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:calling disconnected_handler 0x804d190 for fd 11
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:done calling disconnected_handler 0x804d190 for fd 11
[ply-event-loop.c]              ply_event_loop_disconnect_source:done disconnecting source with fd 11
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing watches for source with fd 11
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing watches for source with fd 11
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing destinations for source with fd 11
[ply-event-loop.c]   ply_event_loop_free_destinations_for_source:freeing destination (1, 0x804bc20, 0x804d190) of fd 11
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing destinations for source with fd 11
[ply-event-loop.c]              ply_event_loop_disconnect_source:removing source with fd 11 from event loop
[ply-event-loop.c]              ply_event_loop_disconnect_source:done removing source with fd 11 from event loop
[ply-boot-server.c]                ply_boot_connection_on_request:got update request
[main.c]                                     on_update:updating status to 'network-interface'
[ply-boot-server.c]                ply_boot_connection_on_request:got update request
[main.c]                                     on_update:updating status to 'network-interface-security'
[ply-boot-server.c]                ply_boot_connection_on_request:got update request
[main.c]                                     on_update:updating status to 'network-interface-security'
[ply-boot-server.c]                ply_boot_connection_on_request:got update request
[main.c]                                     on_update:updating status to 'mountall-net'
[ply-boot-server.c]                ply_boot_connection_on_request:got update request
[main.c]                                     on_update:updating status to 'failsafe'
[ply-event-loop.c]              ply_event_loop_disconnect_source:disconnecting source with fd 13
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:calling disconnected_handler 0x804d190 for fd 13
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:done calling disconnected_handler 0x804d190 for fd 13
[ply-event-loop.c]              ply_event_loop_disconnect_source:done disconnecting source with fd 13
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing watches for source with fd 13
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing watches for source with fd 13
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing destinations for source with fd 13
[ply-event-loop.c]   ply_event_loop_free_destinations_for_source:freeing destination (1, 0x804bc20, 0x804d190) of fd 13
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing destinations for source with fd 13
[ply-event-loop.c]              ply_event_loop_disconnect_source:removing source with fd 13 from event loop
[ply-event-loop.c]              ply_event_loop_disconnect_source:done removing source with fd 13 from event loop
[ply-boot-server.c]                ply_boot_connection_on_request:got update request
[main.c]                                     on_update:updating status to 'smbd'
[ply-boot-server.c]                ply_boot_connection_on_request:got update request
[main.c]                                     on_update:updating status to 'mountall-net'
[ply-boot-server.c]                ply_boot_connection_on_request:got update request
[main.c]                                     on_update:updating status to 'network-interface'
[ply-boot-server.c]                ply_boot_connection_on_request:got update request
[main.c]                                     on_update:updating status to 'failsafe'
[ply-boot-server.c]                ply_boot_connection_on_request:got update request
[main.c]                                     on_update:updating status to 'rc-sysinit'
[ply-event-loop.c]              ply_event_loop_disconnect_source:disconnecting source with fd 13
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:calling disconnected_handler 0x804d190 for fd 13
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:done calling disconnected_handler 0x804d190 for fd 13
[ply-event-loop.c]              ply_event_loop_disconnect_source:done disconnecting source with fd 13
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing watches for source with fd 13
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing watches for source with fd 13
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing destinations for source with fd 13
[ply-event-loop.c]   ply_event_loop_free_destinations_for_source:freeing destination (1, 0x804bc20, 0x804d190) of fd 13
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing destinations for source with fd 13
[ply-event-loop.c]              ply_event_loop_disconnect_source:removing source with fd 13 from event loop
[ply-event-loop.c]              ply_event_loop_disconnect_source:done removing source with fd 13 from event loop
[ply-boot-server.c]                ply_boot_connection_on_request:got update request
[main.c]                                     on_update:updating status to 'upstart-socket-bridge'
[ply-event-loop.c]              ply_event_loop_disconnect_source:disconnecting source with fd 13
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:calling disconnected_handler 0x804d190 for fd 13
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:done calling disconnected_handler 0x804d190 for fd 13
[ply-event-loop.c]              ply_event_loop_disconnect_source:done disconnecting source with fd 13
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing watches for source with fd 13
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing watches for source with fd 13
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing destinations for source with fd 13
[ply-event-loop.c]   ply_event_loop_free_destinations_for_source:freeing destination (1, 0x804bc20, 0x804d190) of fd 13
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing destinations for source with fd 13
[ply-event-loop.c]              ply_event_loop_disconnect_source:removing source with fd 13 from event loop
[ply-event-loop.c]              ply_event_loop_disconnect_source:done removing source with fd 13 from event loop
[ply-event-loop.c]              ply_event_loop_disconnect_source:disconnecting source with fd 13
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:calling disconnected_handler 0x804d190 for fd 13
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:done calling disconnected_handler 0x804d190 for fd 13
[ply-event-loop.c]              ply_event_loop_disconnect_source:done disconnecting source with fd 13
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing watches for source with fd 13
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing watches for source with fd 13
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing destinations for source with fd 13
[ply-event-loop.c]   ply_event_loop_free_destinations_for_source:freeing destination (1, 0x804bc20, 0x804d190) of fd 13
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing destinations for source with fd 13
[ply-event-loop.c]              ply_event_loop_disconnect_source:removing source with fd 13 from event loop
[ply-event-loop.c]              ply_event_loop_disconnect_source:done removing source with fd 13 from event loop
[ply-boot-server.c]                ply_boot_connection_on_request:got update request
[main.c]                                     on_update:updating status to 'network-interface-security'
[ply-boot-server.c]                ply_boot_connection_on_request:got update request
[main.c]                                     on_update:updating status to 'network-interface'
[ply-event-loop.c]              ply_event_loop_disconnect_source:disconnecting source with fd 13
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:calling disconnected_handler 0x804d190 for fd 13
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:done calling disconnected_handler 0x804d190 for fd 13
[ply-event-loop.c]              ply_event_loop_disconnect_source:done disconnecting source with fd 13
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing watches for source with fd 13
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing watches for source with fd 13
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing destinations for source with fd 13
[ply-event-loop.c]   ply_event_loop_free_destinations_for_source:freeing destination (1, 0x804bc20, 0x804d190) of fd 13
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing destinations for source with fd 13
[ply-event-loop.c]              ply_event_loop_disconnect_source:removing source with fd 13 from event loop
[ply-event-loop.c]              ply_event_loop_disconnect_source:done removing source with fd 13 from event loop
[ply-event-loop.c]              ply_event_loop_disconnect_source:disconnecting source with fd 13
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:calling disconnected_handler 0x804d190 for fd 13
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:done calling disconnected_handler 0x804d190 for fd 13
[ply-event-loop.c]              ply_event_loop_disconnect_source:done disconnecting source with fd 13
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing watches for source with fd 13
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing watches for source with fd 13
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing destinations for source with fd 13
[ply-event-loop.c]   ply_event_loop_free_destinations_for_source:freeing destination (1, 0x804bc20, 0x804d190) of fd 13
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing destinations for source with fd 13
[ply-event-loop.c]              ply_event_loop_disconnect_source:removing source with fd 13 from event loop
[ply-event-loop.c]              ply_event_loop_disconnect_source:done removing source with fd 13 from event loop
[ply-boot-server.c]                ply_boot_connection_on_request:got update request
[main.c]                                     on_update:updating status to 'rc-sysinit'
[ply-event-loop.c]              ply_event_loop_disconnect_source:disconnecting source with fd 13
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:calling disconnected_handler 0x804d190 for fd 13
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:done calling disconnected_handler 0x804d190 for fd 13
[ply-event-loop.c]              ply_event_loop_disconnect_source:done disconnecting source with fd 13
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing watches for source with fd 13
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing watches for source with fd 13
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing destinations for source with fd 13
[ply-event-loop.c]   ply_event_loop_free_destinations_for_source:freeing destination (1, 0x804bc20, 0x804d190) of fd 13
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing destinations for source with fd 13
[ply-event-loop.c]              ply_event_loop_disconnect_source:removing source with fd 13 from event loop
[ply-event-loop.c]              ply_event_loop_disconnect_source:done removing source with fd 13 from event loop
[ply-boot-server.c]                ply_boot_connection_on_request:got has_active vt? request
[ply-event-loop.c]              ply_event_loop_disconnect_source:disconnecting source with fd 13
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:calling disconnected_handler 0x804d190 for fd 13
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:done calling disconnected_handler 0x804d190 for fd 13
[ply-event-loop.c]              ply_event_loop_disconnect_source:done disconnecting source with fd 13
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing watches for source with fd 13
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing watches for source with fd 13
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing destinations for source with fd 13
[ply-event-loop.c]   ply_event_loop_free_destinations_for_source:freeing destination (1, 0x804bc20, 0x804d190) of fd 13
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing destinations for source with fd 13
[ply-event-loop.c]              ply_event_loop_disconnect_source:removing source with fd 13 from event loop
[ply-event-loop.c]              ply_event_loop_disconnect_source:done removing source with fd 13 from event loop
[ply-event-loop.c]              ply_event_loop_disconnect_source:disconnecting source with fd 14
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:calling disconnected_handler 0x804d190 for fd 14
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:done calling disconnected_handler 0x804d190 for fd 14
[ply-event-loop.c]              ply_event_loop_disconnect_source:done disconnecting source with fd 14
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing watches for source with fd 14
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing watches for source with fd 14
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing destinations for source with fd 14
[ply-event-loop.c]   ply_event_loop_free_destinations_for_source:freeing destination (1, 0x804bc20, 0x804d190) of fd 14
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing destinations for source with fd 14
[ply-event-loop.c]              ply_event_loop_disconnect_source:removing source with fd 14 from event loop
[ply-event-loop.c]              ply_event_loop_disconnect_source:done removing source with fd 14 from event loop
[ply-boot-server.c]                ply_boot_connection_on_request:got deactivate request
[main.c]                                 on_deactivate:deactivating
[ply-boot-splash.c]                   ply_boot_splash_become_idle:telling splash to become idle
[ply-boot-splash.c]                                       on_idle:splash now idle
[ply-boot-server.c]                ply_boot_connection_on_request:got update request
[main.c]                                     on_update:updating status to 'rc'
[ply-boot-server.c]                ply_boot_connection_on_request:got update request
[main.c]                                     on_update:updating status to 'tty4'
[ply-boot-server.c]                ply_boot_connection_on_request:got update request
[main.c]                                     on_update:updating status to 'apport'
[ply-boot-server.c]                ply_boot_connection_on_request:got update request
[main.c]                                     on_update:updating status to 'tty5'
[ply-boot-server.c]                ply_boot_connection_on_request:got update request
[main.c]                                     on_update:updating status to 'gdm'
[ply-boot-server.c]                ply_boot_connection_on_request:got update request
[main.c]                                     on_update:updating status to 'lightdm'
[ply-boot-server.c]                ply_boot_connection_on_request:got update request
[main.c]                                     on_update:updating status to 'acpid'
[ply-boot-server.c]                ply_boot_connection_on_request:got update request
[main.c]                                     on_update:updating status to 'anacron'
[ply-boot-server.c]                ply_boot_connection_on_request:got update request
[main.c]                                     on_update:updating status to 'cron'
[ply-boot-server.c]                ply_boot_connection_on_request:got update request
[main.c]                                     on_update:updating status to 'atd'
[ply-boot-server.c]                ply_boot_connection_on_request:got update request
[main.c]                                     on_update:updating status to 'tty2'
[ply-boot-server.c]                ply_boot_connection_on_request:got update request
[main.c]                                     on_update:updating status to 'tty3'
[ply-boot-server.c]                ply_boot_connection_on_request:got update request
[main.c]                                     on_update:updating status to 'dmesg'
[ply-boot-server.c]                ply_boot_connection_on_request:got update request
[main.c]                                     on_update:updating status to 'tty6'
[ply-boot-server.c]                ply_boot_connection_on_request:got update request
[main.c]                                     on_update:updating status to 'plymouth-stop'
[ply-boot-server.c]                ply_boot_connection_on_request:got update request
[main.c]                                     on_update:updating status to 'irqbalance'
[main.c]                           on_boot_splash_idle:boot splash idle
[main.c]                           on_boot_splash_idle:deactivating splash
[main.c]                             deactivate_splash:deactivating renderer
[./plugin.c]                                    deactivate:dropping master
[main.c]                             deactivate_splash:deactivating keyboard
[ply-event-loop.c]               ply_event_loop_stop_watching_fd:stopping watching fd 10
[ply-event-loop.c]               ply_event_loop_stop_watching_fd:removing destination for fd 10
[main.c]                             deactivate_splash:deactivating terminal session
[ply-terminal-session.c]                   ply_terminal_session_detach:stopping terminal logger
[ply-event-loop.c]               ply_event_loop_stop_watching_fd:stopping watching fd 6
[ply-event-loop.c]               ply_event_loop_stop_watching_fd:removing destination for fd 6
[ply-event-loop.c]               ply_event_loop_stop_watching_fd:no more destinations remaing for fd 6, removing source
[ply-terminal-session.c]                   ply_terminal_session_detach:unredirecting console messages
[ply-terminal-session.c]                   ply_terminal_session_detach:ptmx wasn't originally passed in, destroying created one
[main.c]                             deactivate_splash:deactivating terminal
[ply-boot-server.c]            ply_boot_connection_on_deactivated:deactivated
[ply-event-loop.c]              ply_event_loop_disconnect_source:disconnecting source with fd 13
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:calling disconnected_handler 0x804d190 for fd 13
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:done calling disconnected_handler 0x804d190 for fd 13
[ply-event-loop.c]              ply_event_loop_disconnect_source:done disconnecting source with fd 13
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing watches for source with fd 13
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing watches for source with fd 13
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing destinations for source with fd 13
[ply-event-loop.c]   ply_event_loop_free_destinations_for_source:freeing destination (1, 0x804bc20, 0x804d190) of fd 13
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing destinations for source with fd 13
[ply-event-loop.c]              ply_event_loop_disconnect_source:removing source with fd 13 from event loop
[ply-event-loop.c]              ply_event_loop_disconnect_source:done removing source with fd 13 from event loop
[ply-boot-server.c]                ply_boot_connection_on_request:got update request
[main.c]                                     on_update:updating status to 'gdm'
[ply-event-loop.c]              ply_event_loop_disconnect_source:disconnecting source with fd 6
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:calling disconnected_handler 0x804d190 for fd 6
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:done calling disconnected_handler 0x804d190 for fd 6
[ply-event-loop.c]              ply_event_loop_disconnect_source:done disconnecting source with fd 6
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing watches for source with fd 6
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing watches for source with fd 6
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing destinations for source with fd 6
[ply-event-loop.c]   ply_event_loop_free_destinations_for_source:freeing destination (1, 0x804bc20, 0x804d190) of fd 6
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing destinations for source with fd 6
[ply-event-loop.c]              ply_event_loop_disconnect_source:removing source with fd 6 from event loop
[ply-event-loop.c]              ply_event_loop_disconnect_source:done removing source with fd 6 from event loop
[ply-boot-server.c]                ply_boot_connection_on_request:got update request
[main.c]                                     on_update:updating status to 'dmesg'
[ply-boot-server.c]                ply_boot_connection_on_request:got update request
[main.c]                                     on_update:updating status to 'anacron'
[ply-boot-server.c]                ply_boot_connection_on_request:got update request
[main.c]                                     on_update:updating status to 'anacron'
[ply-boot-server.c]                ply_boot_connection_on_request:got update request
[main.c]                                     on_update:updating status to 'anacron'
[ply-boot-server.c]                ply_boot_connection_on_request:got update request
[main.c]                                     on_update:updating status to 'udevtrigger'
[ply-boot-server.c]                ply_boot_connection_on_request:got update request
[main.c]                                     on_update:updating status to 'udevmonitor'
[ply-boot-server.c]                ply_boot_connection_on_request:got update request
[main.c]                                     on_update:updating status to 'cryptdisks-enable'
[ply-boot-server.c]                ply_boot_connection_on_request:got update request
[main.c]                                     on_update:updating status to 'network-interface-security'
[ply-boot-server.c]                ply_boot_connection_on_request:got message request
[main.c]                            on_display_message:displaying message The disk drive for /dev/mapper/cryptswap1 is not ready yet or not present.
[ply-boot-server.c]                ply_boot_connection_on_request:got message request
[main.c]                            on_display_message:displaying message keys:Continue to wait, or Press S to skip mounting or M for manual recovery
[ply-boot-server.c]                ply_boot_connection_on_request:got keystroke request
[main.c]                        on_watch_for_keystroke:watching for keystroke
[ply-event-loop.c]              ply_event_loop_disconnect_source:disconnecting source with fd 6
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:calling disconnected_handler 0x804d190 for fd 6
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:done calling disconnected_handler 0x804d190 for fd 6
[ply-event-loop.c]              ply_event_loop_disconnect_source:done disconnecting source with fd 6
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing watches for source with fd 6
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing watches for source with fd 6
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing destinations for source with fd 6
[ply-event-loop.c]   ply_event_loop_free_destinations_for_source:freeing destination (1, 0x804bc20, 0x804d190) of fd 6
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing destinations for source with fd 6
[ply-event-loop.c]              ply_event_loop_disconnect_source:removing source with fd 6 from event loop
[ply-event-loop.c]              ply_event_loop_disconnect_source:done removing source with fd 6 from event loop
[ply-event-loop.c]              ply_event_loop_disconnect_source:disconnecting source with fd 6
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:calling disconnected_handler 0x804d190 for fd 6
[ply-event-loop.c]   ply_event_loop_handle_disconnect_for_source:done calling disconnected_handler 0x804d190 for fd 6
[ply-event-loop.c]              ply_event_loop_disconnect_source:done disconnecting source with fd 6
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing watches for source with fd 6
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing watches for source with fd 6
[ply-event-loop.c]              ply_event_loop_disconnect_source:freeing destinations for source with fd 6
[ply-event-loop.c]   ply_event_loop_free_destinations_for_source:freeing destination (1, 0x804bc20, 0x804d190) of fd 6
[ply-event-loop.c]              ply_event_loop_disconnect_source:done freeing destinations for source with fd 6
[ply-event-loop.c]              ply_event_loop_disconnect_source:removing source with fd 6 from event loop
[ply-event-loop.c]              ply_event_loop_disconnect_source:done removing source with fd 6 from event loop
[ply-boot-server.c]                ply_boot_connection_on_request:got quit --retain-splash request
[main.c]                                       on_quit:time to quit, closing log
[main.c]                                       on_quit:unloading splash
[ply-boot-splash.c]                   ply_boot_splash_become_idle:telling splash to become idle
[ply-boot-splash.c]                                       on_idle:splash now idle
[main.c]                           on_boot_splash_idle:boot splash idle
[main.c]                           on_boot_splash_idle:quitting splash
[main.c]                                   quit_splash:quiting splash
[main.c]                                   quit_splash:freeing splash
[ply-boot-splash.c]                          ply_boot_splash_free:freeing splash
[ply-boot-splash.c]                               remove_displays:removing pixel displays
[ply-boot-splash.c]                               remove_displays:Removing 1366x768 pixel display
[ply-boot-splash.c]                               remove_displays:Removing node
[ply-boot-splash.c]                               remove_displays:removing text displays
[ply-boot-splash.c]                               remove_displays:Removing 170x48 text display
[ply-boot-splash.c]                               remove_displays:Removing node
[main.c]                                   quit_splash:removing displays and keyboard
[main.c]                  remove_displays_and_keyboard:removing displays and keyboard
[main.c]                  remove_displays_and_keyboard:removing pixel display
[main.c]                  remove_displays_and_keyboard:removing text display
[main.c]                  remove_displays_and_keyboard:removing keyboard
[./plugin.c]                       ply_renderer_head_unmap:unmapping 1366x768 renderer head
[./plugin.c]                                  close_device:closing device
[./plugin.c]                        ply_renderer_head_free:freeing 1366x768 renderer head
[./plugin.c]                                 unload_driver:unloading driver
[./ply-renderer-i915-driver.c]                                destroy_driver:uninitializing intel buffer manager
[ply-renderer.c]                             ply_renderer_free:Unloading renderer backend plugin
[ply-terminal.c]                            ply_terminal_close:restoring color palette
[ply-terminal.c]                            ply_terminal_close:stop watching tty fd
[ply-event-loop.c]               ply_event_loop_stop_watching_fd:stopping watching fd 10
[ply-event-loop.c]               ply_event_loop_stop_watching_fd:removing destination for fd 10
[ply-event-loop.c]               ply_event_loop_stop_watching_fd:no more destinations remaing for fd 10, removing source
[ply-terminal.c]                            ply_terminal_close:stop watching SIGWINCH signal
[ply-terminal.c]                            ply_terminal_close:setting buffered input
[main.c]                                   quit_splash:detaching session
[ply-terminal-session.c]                   ply_terminal_session_detach:stopping terminal logger
[main.c]                           on_boot_splash_idle:quitting program
[main.c]                                  quit_program:exiting event loop
[ply-boot-server.c]          ply_boot_connection_on_quit_complete:quit complete
[main.c]                                          main:exited event loop
[main.c]                       get_cache_file_for_mode:returning cache file '/var/lib/plymouth//boot-duration'
[ply-boot-splash.c]                          ply_boot_splash_free:freeing splash
[main.c]                                          main:freeing terminal session
[main.c]                                          main:exiting with code 0

---

