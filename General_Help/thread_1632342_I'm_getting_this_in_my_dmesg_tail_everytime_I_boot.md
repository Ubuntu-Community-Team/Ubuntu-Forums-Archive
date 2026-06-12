---
title: "I'm getting this in my dmesg tail everytime I boot"
date: 2010-11-27
forum: General Help
---

### Post by lordskid on 2010-11-27
ACPI: EC: GPE storm detected, transactions will use polling mode

Anybody knows what is causing this or is this even a problem? The only thing I noticed is that my atheros 9285's bluetooth does not work. Is that somehow related to this? or is this because of the change of state of battery? charging/draining?

---

### Post by c00lwaterz on 2010-11-27
[123938.416091] =====>rtl8192_set_chan()====ch:1
[123938.426076] ===>rtl8192se_link_change():ieee->iw_mode is 2
[123938.426083] rtl8192_update_cap(): WLAN_CAPABILITY_LONG_PREAMBLE
[123946.183325] =====>rtllib_sta_ps(): no need to ps,wake up!! ieee->ps is 0,ieee->iw_mode is 2,ieee->state is 5
[124030.558996] rtl8192_hw_sleep_down(): RF Change in progress!
[124056.902000] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[124056.902079] ===>rtl8192se_link_change():ieee->iw_mode is 2
[124056.956077] =====>rtl8192_set_chan()====ch:1
[124057.068044] =====>rtl8192_set_chan()====ch:2
[124057.180043] =====>rtl8192_set_chan()====ch:3
[124057.292040] =====>rtl8192_set_chan()====ch:4
[124057.404042] =====>rtl8192_set_chan()====ch:5
[124057.516039] =====>rtl8192_set_chan()====ch:6
[124057.628240] =====>rtl8192_set_chan()====ch:7
[124057.741032] =====>rtl8192_set_chan()====ch:8
[124057.852052] =====>rtl8192_set_chan()====ch:9
[124057.964049] =====>rtl8192_set_chan()====ch:10
[124058.076053] =====>rtl8192_set_chan()====ch:11
[124058.188043] =====>rtl8192_set_chan()====ch:12
[124058.300241] =====>rtl8192_set_chan()====ch:13
[124058.412273] =====>rtl8192_set_chan()====ch:1
[124058.422255] ===>rtl8192se_link_change():ieee->iw_mode is 2
[124058.422262] rtl8192_update_cap(): WLAN_CAPABILITY_LONG_PREAMBLE
[124086.673021] rtl8192_hw_sleep_down(): RF Change in progress!
[124114.729998] rtl8192_hw_sleep_down(): RF Change in progress!
[124176.905588] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[124176.905670] ===>rtl8192se_link_change():ieee->iw_mode is 2
[124176.960057] =====>rtl8192_set_chan()====ch:1
[124177.072237] =====>rtl8192_set_chan()====ch:2
[124177.184071] =====>rtl8192_set_chan()====ch:3
[124177.296086] =====>rtl8192_set_chan()====ch:4
[124177.408039] =====>rtl8192_set_chan()====ch:5
[124177.520238] =====>rtl8192_set_chan()====ch:6
[124177.632937] =====>rtl8192_set_chan()====ch:7
[124177.744242] =====>rtl8192_set_chan()====ch:8
[124177.856042] =====>rtl8192_set_chan()====ch:9
[124177.968239] =====>rtl8192_set_chan()====ch:10
[124178.080038] =====>rtl8192_set_chan()====ch:11
[124178.195820] =====>rtl8192_set_chan()====ch:12
[124178.308023] =====>rtl8192_set_chan()====ch:13
[124178.420060] =====>rtl8192_set_chan()====ch:1
[124178.430042] ===>rtl8192se_link_change():ieee->iw_mode is 2
[124178.430047] rtl8192_update_cap(): WLAN_CAPABILITY_LONG_PREAMBLE
[124190.872636] MgntActSet_RF_State(): RF Change in progress! Wait to set..StateToSet(0).
[124232.964787] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[124270.992590] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[124287.065511] rtl8192_hw_sleep_down(): RF Change in progress!
[124296.903907] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[124296.904008] ===>rtl8192se_link_change():ieee->iw_mode is 2
[124296.960112] =====>rtl8192_set_chan()====ch:1
[124297.072587] =====>rtl8192_set_chan()====ch:2
[124297.184588] =====>rtl8192_set_chan()====ch:3
[124297.296088] =====>rtl8192_set_chan()====ch:4
[124297.408725] =====>rtl8192_set_chan()====ch:5
[124297.520544] =====>rtl8192_set_chan()====ch:6
[124297.632563] =====>rtl8192_set_chan()====ch:7
[124297.744076] =====>rtl8192_set_chan()====ch:8
[124297.856573] =====>rtl8192_set_chan()====ch:9
[124297.968588] =====>rtl8192_set_chan()====ch:10
[124298.080591] =====>rtl8192_set_chan()====ch:11
[124298.192081] =====>rtl8192_set_chan()====ch:12
[124298.304590] =====>rtl8192_set_chan()====ch:13
[124298.416276] =====>rtl8192_set_chan()====ch:1
[124298.426256] ===>rtl8192se_link_change():ieee->iw_mode is 2
[124298.426263] rtl8192_update_cap(): WLAN_CAPABILITY_LONG_PREAMBLE
[124299.662146] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[124389.874547] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[124412.606954] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[124416.901381] ===>rtl8192se_link_change():ieee->iw_mode is 2
[124416.956082] =====>rtl8192_set_chan()====ch:1
[124417.068041] =====>rtl8192_set_chan()====ch:2
[124417.180540] =====>rtl8192_set_chan()====ch:3
[124417.292040] =====>rtl8192_set_chan()====ch:4
[124417.404053] =====>rtl8192_set_chan()====ch:5
[124417.516040] =====>rtl8192_set_chan()====ch:6
[124417.628040] =====>rtl8192_set_chan()====ch:7
[124417.740247] =====>rtl8192_set_chan()====ch:8
[124417.852044] =====>rtl8192_set_chan()====ch:9
[124417.964040] =====>rtl8192_set_chan()====ch:10
[124418.076039] =====>rtl8192_set_chan()====ch:11
[124418.188240] =====>rtl8192_set_chan()====ch:12
[124418.300053] =====>rtl8192_set_chan()====ch:13
[124418.412383] =====>rtl8192_set_chan()====ch:1
[124418.422369] ===>rtl8192se_link_change():ieee->iw_mode is 2
[124418.422376] rtl8192_update_cap(): WLAN_CAPABILITY_LONG_PREAMBLE
[124447.388036] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[124461.412455] MgntActSet_RF_State(): RF Change in progress! Wait to set..StateToSet(0).
[124462.474676] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[124466.059542] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[124497.493039] rtl8192_hw_sleep_down(): RF Change in progress!
[124536.901587] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[124536.901666] ===>rtl8192se_link_change():ieee->iw_mode is 2
[124536.956081] =====>rtl8192_set_chan()====ch:1
[124537.068281] =====>rtl8192_set_chan()====ch:2
[124537.180064] =====>rtl8192_set_chan()====ch:3
[124537.292050] =====>rtl8192_set_chan()====ch:4
[124537.404054] =====>rtl8192_set_chan()====ch:5
[124537.516044] =====>rtl8192_set_chan()====ch:6
[124537.628049] =====>rtl8192_set_chan()====ch:7
[124537.740043] =====>rtl8192_set_chan()====ch:8
[124537.852063] =====>rtl8192_set_chan()====ch:9
[124537.964035] =====>rtl8192_set_chan()====ch:10
[124538.076057] =====>rtl8192_set_chan()====ch:11
[124538.188239] =====>rtl8192_set_chan()====ch:12
[124538.300712] =====>rtl8192_set_chan()====ch:13
[124538.412064] =====>rtl8192_set_chan()====ch:1
[124538.422045] ===>rtl8192se_link_change():ieee->iw_mode is 2
[124538.422051] rtl8192_update_cap(): WLAN_CAPABILITY_LONG_PREAMBLE
[124573.636457] MgntActSet_RF_State(): RF Change in progress! Wait to set..StateToSet(0).
[124656.905804] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[124656.905906] ===>rtl8192se_link_change():ieee->iw_mode is 2
[124656.960605] =====>rtl8192_set_chan()====ch:1
[124657.072283] =====>rtl8192_set_chan()====ch:2
[124657.184064] =====>rtl8192_set_chan()====ch:3
[124657.296589] =====>rtl8192_set_chan()====ch:4
[124657.408081] =====>rtl8192_set_chan()====ch:5
[124657.520761] =====>rtl8192_set_chan()====ch:6
[124657.632278] =====>rtl8192_set_chan()====ch:7
[124657.744575] =====>rtl8192_set_chan()====ch:8
[124657.856083] =====>rtl8192_set_chan()====ch:9
[124657.968087] =====>rtl8192_set_chan()====ch:10
[124658.080228] =====>rtl8192_set_chan()====ch:11
[124658.192064] =====>rtl8192_set_chan()====ch:12
[124658.304591] =====>rtl8192_set_chan()====ch:13
[124658.416285] =====>rtl8192_set_chan()====ch:1
[124658.426265] ===>rtl8192se_link_change():ieee->iw_mode is 2
[124658.426271] rtl8192_update_cap(): WLAN_CAPABILITY_LONG_PREAMBLE
[124669.828573] rtl8192_hw_sleep_down(): RF Change in progress!
[124699.895258] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[124711.914072] rtl8192_hw_sleep_down(): RF Change in progress!
[124741.980036] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[124753.999574] rtl8192_hw_sleep_down(): RF Change in progress!
[124776.904650] ===>rtl8192se_link_change():ieee->iw_mode is 2
[124776.960072] =====>rtl8192_set_chan()====ch:1
[124777.072042] =====>rtl8192_set_chan()====ch:2
[124777.184062] =====>rtl8192_set_chan()====ch:3
[124777.296054] =====>rtl8192_set_chan()====ch:4
[124777.408241] =====>rtl8192_set_chan()====ch:5
[124777.520185] =====>rtl8192_set_chan()====ch:6
[124777.632124] =====>rtl8192_set_chan()====ch:7
[124777.744057] =====>rtl8192_set_chan()====ch:8
[124777.856024] =====>rtl8192_set_chan()====ch:9
[124777.968254] =====>rtl8192_set_chan()====ch:10
[124778.080050] =====>rtl8192_set_chan()====ch:11
[124778.192038] =====>rtl8192_set_chan()====ch:12
[124778.304038] =====>rtl8192_set_chan()====ch:13
[124778.416261] =====>rtl8192_set_chan()====ch:1
[124778.426244] ===>rtl8192se_link_change():ieee->iw_mode is 2
[124778.426250] rtl8192_update_cap(): WLAN_CAPABILITY_LONG_PREAMBLE
[124795.574792] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[124810.113572] rtl8192_hw_sleep_down(): RF Change in progress!
[124824.142074] rtl8192_hw_sleep_down(): RF Change in progress!
[124835.714690] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[124838.170580] rtl8192_hw_sleep_down(): RF Change in progress!
[124844.011276] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[124861.109605] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[124880.256085] rtl8192_hw_sleep_down(): RF Change in progress!
[124889.066009] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[124896.904063] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[124896.904140] ===>rtl8192se_link_change():ieee->iw_mode is 2
[124896.960109] =====>rtl8192_set_chan()====ch:1
[124897.072253] =====>rtl8192_set_chan()====ch:2
[124897.184784] =====>rtl8192_set_chan()====ch:3
[124897.298152] =====>rtl8192_set_chan()====ch:4
[124897.408084] =====>rtl8192_set_chan()====ch:5
[124897.520063] =====>rtl8192_set_chan()====ch:6
[124897.632403] =====>rtl8192_set_chan()====ch:7
[124897.744278] =====>rtl8192_set_chan()====ch:8
[124897.856546] =====>rtl8192_set_chan()====ch:9
[124897.968777] =====>rtl8192_set_chan()====ch:10
[124898.080230] =====>rtl8192_set_chan()====ch:11
[124898.192775] =====>rtl8192_set_chan()====ch:12
[124898.304078] =====>rtl8192_set_chan()====ch:13
[124898.416285] =====>rtl8192_set_chan()====ch:1
[124898.426274] ===>rtl8192se_link_change():ieee->iw_mode is 2
[124898.426280] rtl8192_update_cap(): WLAN_CAPABILITY_LONG_PREAMBLE
[124900.288652] MgntActSet_RF_State(): RF Change in progress! Wait to set..StateToSet(0).
[124922.341584] rtl8192_hw_sleep_down(): RF Change in progress!
[125036.912168] ===>rtl8192se_link_change():ieee->iw_mode is 2
[125036.968076] =====>rtl8192_set_chan()====ch:1
[125037.080044] =====>rtl8192_set_chan()====ch:2
[125037.192048] =====>rtl8192_set_chan()====ch:3
[125037.304265] =====>rtl8192_set_chan()====ch:4
[125037.416052] =====>rtl8192_set_chan()====ch:5
[125037.528054] =====>rtl8192_set_chan()====ch:6
[125037.640052] =====>rtl8192_set_chan()====ch:7
[125037.752048] =====>rtl8192_set_chan()====ch:8
[125037.864040] =====>rtl8192_set_chan()====ch:9
[125037.976044] =====>rtl8192_set_chan()====ch:10
[125038.088040] =====>rtl8192_set_chan()====ch:11
[125038.200043] =====>rtl8192_set_chan()====ch:12
[125038.312045] =====>rtl8192_set_chan()====ch:13
[125038.424047] =====>rtl8192_set_chan()====ch:1
[125038.434029] ===>rtl8192se_link_change():ieee->iw_mode is 2
[125038.434035] rtl8192_update_cap(): WLAN_CAPABILITY_LONG_PREAMBLE
[125317.015394] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[125317.015480] ===>rtl8192se_link_change():ieee->iw_mode is 2
[125317.068191] =====>rtl8192_set_chan()====ch:1
[125317.180150] =====>rtl8192_set_chan()====ch:2
[125317.292163] =====>rtl8192_set_chan()====ch:3
[125317.404149] =====>rtl8192_set_chan()====ch:4
[125317.516160] =====>rtl8192_set_chan()====ch:5
[125317.628246] =====>rtl8192_set_chan()====ch:6
[125317.740244] =====>rtl8192_set_chan()====ch:7
[125317.852249] =====>rtl8192_set_chan()====ch:8
[125317.964146] =====>rtl8192_set_chan()====ch:9
[125318.076239] =====>rtl8192_set_chan()====ch:10
[125318.188256] =====>rtl8192_set_chan()====ch:11
[125318.300155] =====>rtl8192_set_chan()====ch:12
[125318.412247] =====>rtl8192_set_chan()====ch:13
[125318.524200] =====>rtl8192_set_chan()====ch:1
[125318.534179] ===>rtl8192se_link_change():ieee->iw_mode is 2
[125318.534184] rtl8192_update_cap(): WLAN_CAPABILITY_LONG_PREAMBLE
[125319.133689] rtl8192_hw_sleep_down(): RF Change in progress!
[125376.906036] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[125376.906115] ===>rtl8192se_link_change():ieee->iw_mode is 2
[125376.960300] =====>rtl8192_set_chan()====ch:1
[125377.072276] =====>rtl8192_set_chan()====ch:2
[125377.184096] =====>rtl8192_set_chan()====ch:3
[125377.296274] =====>rtl8192_set_chan()====ch:4
[125377.408096] =====>rtl8192_set_chan()====ch:5
[125377.520093] =====>rtl8192_set_chan()====ch:6
[125377.632271] =====>rtl8192_set_chan()====ch:7
[125377.744274] =====>rtl8192_set_chan()====ch:8
[125377.856277] =====>rtl8192_set_chan()====ch:9
[125377.968096] =====>rtl8192_set_chan()====ch:10
[125378.080271] =====>rtl8192_set_chan()====ch:11
[125378.192095] =====>rtl8192_set_chan()====ch:12
[125378.304107] =====>rtl8192_set_chan()====ch:13
[125378.416209] =====>rtl8192_set_chan()====ch:1
[125378.426185] ===>rtl8192se_link_change():ieee->iw_mode is 2
[125378.426191] rtl8192_update_cap(): WLAN_CAPABILITY_LONG_PREAMBLE
[125381.248616] MgntActSet_RF_State(): RF Change in progress! Wait to set..StateToSet(0).
[125423.332613] MgntActSet_RF_State(): RF Change in progress! Wait to set..StateToSet(0).
[125465.424033] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[125477.440204] rtl8192_hw_sleep_down(): RF Change in progress!
[125496.905613] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[125496.905704] ===>rtl8192se_link_change():ieee->iw_mode is 2
[125496.960292] =====>rtl8192_set_chan()====ch:1
[125497.072282] =====>rtl8192_set_chan()====ch:2
[125497.184251] =====>rtl8192_set_chan()====ch:3
[125497.296273] =====>rtl8192_set_chan()====ch:4
[125497.408271] =====>rtl8192_set_chan()====ch:5
[125497.520083] =====>rtl8192_set_chan()====ch:6
[125497.632275] =====>rtl8192_set_chan()====ch:7
[125497.744275] =====>rtl8192_set_chan()====ch:8
[125497.856275] =====>rtl8192_set_chan()====ch:9
[125497.968082] =====>rtl8192_set_chan()====ch:10
[125498.080281] =====>rtl8192_set_chan()====ch:11
[125498.192079] =====>rtl8192_set_chan()====ch:12
[125498.304078] =====>rtl8192_set_chan()====ch:13
[125498.416283] =====>rtl8192_set_chan()====ch:1
[125498.426261] ===>rtl8192se_link_change():ieee->iw_mode is 2
[125498.426267] rtl8192_update_cap(): WLAN_CAPABILITY_LONG_PREAMBLE
[125507.508034] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[125519.525713] rtl8192_hw_sleep_down(): RF Change in progress!
[125549.592035] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[125561.611225] rtl8192_hw_sleep_down(): RF Change in progress!
[125603.696726] rtl8192_hw_sleep_down(): RF Change in progress!
[125616.901206] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[125616.901284] ===>rtl8192se_link_change():ieee->iw_mode is 2
[125616.956293] =====>rtl8192_set_chan()====ch:1
[125617.068255] =====>rtl8192_set_chan()====ch:2
[125617.180258] =====>rtl8192_set_chan()====ch:3
[125617.292252] =====>rtl8192_set_chan()====ch:4
[125617.404263] =====>rtl8192_set_chan()====ch:5
[125617.516273] =====>rtl8192_set_chan()====ch:6
[125617.628752] =====>rtl8192_set_chan()====ch:7
[125617.740248] =====>rtl8192_set_chan()====ch:8
[125617.852283] =====>rtl8192_set_chan()====ch:9
[125617.964273] =====>rtl8192_set_chan()====ch:10
[125618.076253] =====>rtl8192_set_chan()====ch:11
[125618.188254] =====>rtl8192_set_chan()====ch:12
[125618.300244] =====>rtl8192_set_chan()====ch:13
[125618.412284] =====>rtl8192_set_chan()====ch:1
[125618.422260] ===>rtl8192se_link_change():ieee->iw_mode is 2
[125618.422267] rtl8192_update_cap(): WLAN_CAPABILITY_LONG_PREAMBLE
[125645.782234] rtl8192_hw_sleep_down(): RF Change in progress!
[125687.867743] rtl8192_hw_sleep_down(): RF Change in progress!
[125729.953253] rtl8192_hw_sleep_down(): RF Change in progress!
[125736.905781] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[125736.905883] ===>rtl8192se_link_change():ieee->iw_mode is 2
[125736.960767] =====>rtl8192_set_chan()====ch:1
[125737.072563] =====>rtl8192_set_chan()====ch:2
[125737.184759] =====>rtl8192_set_chan()====ch:3
[125737.296746] =====>rtl8192_set_chan()====ch:4
[125737.408265] =====>rtl8192_set_chan()====ch:5
[125737.520206] =====>rtl8192_set_chan()====ch:6
[125737.632779] =====>rtl8192_set_chan()====ch:7
[125737.744566] =====>rtl8192_set_chan()====ch:8
[125737.856560] =====>rtl8192_set_chan()====ch:9
[125737.970213] =====>rtl8192_set_chan()====ch:10
[125738.080773] =====>rtl8192_set_chan()====ch:11
[125738.192287] =====>rtl8192_set_chan()====ch:12
[125738.304174] =====>rtl8192_set_chan()====ch:13
[125738.416276] =====>rtl8192_set_chan()====ch:1
[125738.426257] ===>rtl8192se_link_change():ieee->iw_mode is 2
[125738.426263] rtl8192_update_cap(): WLAN_CAPABILITY_LONG_PREAMBLE
[125764.012650] MgntActSet_RF_State(): RF Change in progress! Wait to set..StateToSet(0).
[125806.100040] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[125848.180629] MgntActSet_RF_State(): RF Change in progress! Wait to set..StateToSet(0).
[125856.905681] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[125856.905766] ===>rtl8192se_link_change():ieee->iw_mode is 2
[125856.960626] =====>rtl8192_set_chan()====ch:1
[125857.072387] =====>rtl8192_set_chan()====ch:2
[125857.184269] =====>rtl8192_set_chan()====ch:3
[125857.296623] =====>rtl8192_set_chan()====ch:4
[125857.408555] =====>rtl8192_set_chan()====ch:5
[125857.520760] =====>rtl8192_set_chan()====ch:6
[125857.632610] =====>rtl8192_set_chan()====ch:7
[125857.744773] =====>rtl8192_set_chan()====ch:8
[125857.856217] =====>rtl8192_set_chan()====ch:9
[125857.968608] =====>rtl8192_set_chan()====ch:10
[125858.080755] =====>rtl8192_set_chan()====ch:11
[125858.192758] =====>rtl8192_set_chan()====ch:12
[125858.304260] =====>rtl8192_set_chan()====ch:13
[125858.416771] =====>rtl8192_set_chan()====ch:1
[125858.426749] ===>rtl8192se_link_change():ieee->iw_mode is 2
[125858.426756] rtl8192_update_cap(): WLAN_CAPABILITY_LONG_PREAMBLE
[125902.288814] rtl8192_hw_sleep_down(): RF Change in progress!
[125932.352041] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[125944.374305] rtl8192_hw_sleep_down(): RF Change in progress!
[125976.905078] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[125976.905169] ===>rtl8192se_link_change():ieee->iw_mode is 2
[125976.960768] =====>rtl8192_set_chan()====ch:1
[125977.072760] =====>rtl8192_set_chan()====ch:2
[125977.184758] =====>rtl8192_set_chan()====ch:3
[125977.296757] =====>rtl8192_set_chan()====ch:4
[125977.408419] =====>rtl8192_set_chan()====ch:5
[125977.520099] =====>rtl8192_set_chan()====ch:6
[125977.632753] =====>rtl8192_set_chan()====ch:7
[125977.744563] =====>rtl8192_set_chan()====ch:8
[125977.856149] =====>rtl8192_set_chan()====ch:9
[125977.968772] =====>rtl8192_set_chan()====ch:10
[125978.080774] =====>rtl8192_set_chan()====ch:11
[125978.192746] =====>rtl8192_set_chan()====ch:12
[125978.304068] =====>rtl8192_set_chan()====ch:13
[125978.416768] =====>rtl8192_set_chan()====ch:1
[125978.426749] ===>rtl8192se_link_change():ieee->iw_mode is 2
[125978.426756] rtl8192_update_cap(): WLAN_CAPABILITY_LONG_PREAMBLE
[125986.459813] rtl8192_hw_sleep_down(): RF Change in progress!
[126028.545323] rtl8192_hw_sleep_down(): RF Change in progress!
[126070.630820] rtl8192_hw_sleep_down(): RF Change in progress!
[126080.155849] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[126086.094605] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[126096.902194] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[126096.902274] ===>rtl8192se_link_change():ieee->iw_mode is 2
[126096.956082] =====>rtl8192_set_chan()====ch:1
[126097.068193] =====>rtl8192_set_chan()====ch:2
[126097.180236] =====>rtl8192_set_chan()====ch:3
[126097.292254] =====>rtl8192_set_chan()====ch:4
[126097.404205] =====>rtl8192_set_chan()====ch:5
[126097.516049] =====>rtl8192_set_chan()====ch:6
[126097.628235] =====>rtl8192_set_chan()====ch:7
[126097.740201] =====>rtl8192_set_chan()====ch:8
[126097.852246] =====>rtl8192_set_chan()====ch:9
[126097.964233] =====>rtl8192_set_chan()====ch:10
[126098.076243] =====>rtl8192_set_chan()====ch:11
[126098.188201] =====>rtl8192_set_chan()====ch:12
[126098.300195] =====>rtl8192_set_chan()====ch:13
[126098.412257] =====>rtl8192_set_chan()====ch:1
[126098.422242] ===>rtl8192se_link_change():ieee->iw_mode is 2
[126098.422248] rtl8192_update_cap(): WLAN_CAPABILITY_LONG_PREAMBLE
[126112.716342] rtl8192_hw_sleep_down(): RF Change in progress!
[126154.801851] rtl8192_hw_sleep_down(): RF Change in progress!
[126216.902092] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[126216.902172] ===>rtl8192se_link_change():ieee->iw_mode is 2
[126216.956265] =====>rtl8192_set_chan()====ch:1
[126217.068061] =====>rtl8192_set_chan()====ch:2
[126217.180235] =====>rtl8192_set_chan()====ch:3
[126217.292109] =====>rtl8192_set_chan()====ch:4
[126217.404071] =====>rtl8192_set_chan()====ch:5
[126217.516059] =====>rtl8192_set_chan()====ch:6
[126217.628768] =====>rtl8192_set_chan()====ch:7
[126217.740069] =====>rtl8192_set_chan()====ch:8
[126217.852250] =====>rtl8192_set_chan()====ch:9
[126217.964064] =====>rtl8192_set_chan()====ch:10
[126218.076074] =====>rtl8192_set_chan()====ch:11
[126218.188073] =====>rtl8192_set_chan()====ch:12
[126218.300064] =====>rtl8192_set_chan()====ch:13
[126218.412081] =====>rtl8192_set_chan()====ch:1
[126218.422065] ===>rtl8192se_link_change():ieee->iw_mode is 2
[126218.422072] rtl8192_update_cap(): WLAN_CAPABILITY_LONG_PREAMBLE
[126230.944767] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[126273.036035] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[126315.116042] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[126327.137411] rtl8192_hw_sleep_down(): RF Change in progress!
[126336.905558] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[126336.905650] ===>rtl8192se_link_change():ieee->iw_mode is 2
[126336.960270] =====>rtl8192_set_chan()====ch:1
[126337.072263] =====>rtl8192_set_chan()====ch:2
[126337.184058] =====>rtl8192_set_chan()====ch:3
[126337.296235] =====>rtl8192_set_chan()====ch:4
[126337.408252] =====>rtl8192_set_chan()====ch:5
[126337.520056] =====>rtl8192_set_chan()====ch:6
[126337.632243] =====>rtl8192_set_chan()====ch:7
[126337.744763] =====>rtl8192_set_chan()====ch:8
[126337.856050] =====>rtl8192_set_chan()====ch:9
[126337.968248] =====>rtl8192_set_chan()====ch:10
[126338.080240] =====>rtl8192_set_chan()====ch:11
[126338.192056] =====>rtl8192_set_chan()====ch:12
[126338.304057] =====>rtl8192_set_chan()====ch:13
[126338.416079] =====>rtl8192_set_chan()====ch:1
[126338.426061] ===>rtl8192se_link_change():ieee->iw_mode is 2
[126338.426067] rtl8192_update_cap(): WLAN_CAPABILITY_LONG_PREAMBLE
[126357.200041] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[126369.222920] rtl8192_hw_sleep_down(): RF Change in progress!
[126411.308443] rtl8192_hw_sleep_down(): RF Change in progress!
[126453.393939] rtl8192_hw_sleep_down(): RF Change in progress!
[126456.902093] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[126456.902169] ===>rtl8192se_link_change():ieee->iw_mode is 2
[126456.956268] =====>rtl8192_set_chan()====ch:1
[126457.068587] =====>rtl8192_set_chan()====ch:2
[126457.180589] =====>rtl8192_set_chan()====ch:3
[126457.292774] =====>rtl8192_set_chan()====ch:4
[126457.406682] =====>rtl8192_set_chan()====ch:5
[126457.520248] =====>rtl8192_set_chan()====ch:6
[126457.632268] =====>rtl8192_set_chan()====ch:7
[126457.744190] =====>rtl8192_set_chan()====ch:8
[126457.856551] =====>rtl8192_set_chan()====ch:9
[126457.968607] =====>rtl8192_set_chan()====ch:10
[126458.080758] =====>rtl8192_set_chan()====ch:11
[126458.192257] =====>rtl8192_set_chan()====ch:12
[126458.304610] =====>rtl8192_set_chan()====ch:13
[126458.416768] =====>rtl8192_set_chan()====ch:1
[126458.426746] ===>rtl8192se_link_change():ieee->iw_mode is 2
[126458.426752] rtl8192_update_cap(): WLAN_CAPABILITY_LONG_PREAMBLE
[126481.450946] rtl8192_hw_sleep_down(): RF Change in progress!
[126495.479448] rtl8192_hw_sleep_down(): RF Change in progress!
[126537.564961] rtl8192_hw_sleep_down(): RF Change in progress!
[126571.624570] MgntActSet_RF_State(): RF Change in progress! Wait to set..StateToSet(0).
[126576.900889] ===>rtl8192se_link_change():ieee->iw_mode is 2
[126576.956565] =====>rtl8192_set_chan()====ch:1
[126577.068203] =====>rtl8192_set_chan()====ch:2
[126577.180136] =====>rtl8192_set_chan()====ch:3
[126577.292188] =====>rtl8192_set_chan()====ch:4
[126577.404273] =====>rtl8192_set_chan()====ch:5
[126577.516278] =====>rtl8192_set_chan()====ch:6
[126577.628281] =====>rtl8192_set_chan()====ch:7
[126577.740289] =====>rtl8192_set_chan()====ch:8
[126577.852277] =====>rtl8192_set_chan()====ch:9
[126577.964274] =====>rtl8192_set_chan()====ch:10
[126578.076188] =====>rtl8192_set_chan()====ch:11
[126578.188183] =====>rtl8192_set_chan()====ch:12
[126578.300180] =====>rtl8192_set_chan()====ch:13
[126578.412205] =====>rtl8192_set_chan()====ch:1
[126578.422181] ===>rtl8192se_link_change():ieee->iw_mode is 2
[126578.422187] rtl8192_update_cap(): WLAN_CAPABILITY_LONG_PREAMBLE
[126589.669961] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
[126613.708453] MgntActSet_RF_State(): RF Change in progress! Wait to set..StateToSet(0).
[126616.515450] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[126636.178204] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
[126650.001573] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData

-

I tried dmesg in terminal and this is the result. I don't know how to use this. why do you use dmesg?
Sorry, I am not that good in linux but i am curious about it.

thanks

---

### Post by hansdown on 2010-11-27
Hi lordskid.

It seems to be an old bug.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/270017](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/270017)

Not sure about a fix.

---

