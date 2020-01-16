# stm32L151_nbiot_tmote_app_spot
> ##### Copyright (C) 2020 Movebroad Version:20.152 Design by Movebroad
> ##### movebroad Kangkang ps: 版本号以下为此版本修改、增加、去除等内容记录！

* 2020-01-16 :
	* 版本号修改为152。
* 2020-01-13 :
	* 发布151固件。
* 2020-01-10 :
	* 同步代码:
	* 算法更新到41,雷达库更新到55,这会让真实车辆的雷达灵敏度更高了。
	* 同时当默认雷达参数异常时可以通过小无线输入 restore 命令进行纠正,然后再点初始化可以修复。
	* 修复inspectconfig.c中bug:最近8秒磁场确实没有波动,然后立刻报告了有车,紧接着下一秒变成了无车,也就是会出现停车时长只有1秒的情况。
	* 修复读取厂牌信息 Vender 异常无法截断,将第4字节添加结束符写'\0'。
* 2020-01-09 :
	* 工作状态下26小时设备数据没发送出去，软件重启设备。
* 2019-12-31 :
	* 注网标记点由参数检出改为注网成功。
	* fifomessage 加入一些调试信息。
* 2019-12-31 :
	* 版本号修改为151。
* 2019-11-20 :
	* CTWING物模型增加标准模型的支持。
* 2019-11-12 :
	* 修复SNR数据范围超出进行取值优化。
* 2019-11-06 :
	* CTWING物模型完成。
* 2019-11-04 :
	* 修复CTWING的接受buf的选择。
	* CTWING物联网模型创建。
* 2019-10-26 :
	* 修复设备倒置休眠中小无线也会发送心跳包数据。
* 2019-10-23 :
	* nb心跳间隔配置由原先可配置最大9小时改为48小时。
* 2019-10-21 :
	* 集成CTWing协议。
* 2019-10-21 :
	* 版本号修改为150。
* 2019-10-21 :
	* 发布149固件。
* 2019-10-18 :
	* 关闭翻转设备发送workinfo包。
	* 倒置休眠中与正放休眠中一样间隔24小时发送info数据。
* 2019-10-10 :
	* MqttSN协议中当消息长度大于100则默认发送成功。
* 2019-10-09 :
	* instpectconfig.c中, < if (status_pre != SpotStatusDataBackUp.spot_status) { > 改为 < if ((status_pre&0x01) != (SpotStatusDataBackUp.spot_status&0x01)) { >。
	* 修复会导致无车心跳之后继续发送无车心跳count会加1。
* 2019-09-27 :
	* NBIOT 限定字符串类参数读取字节数。
* 2019-09-26 :
	* NBIOT 增加指令 QCFG="LWM2M/lifetime"。
	* NBIOT 增加指令 QCHIPINFO。
* 2019-09-25 :
	* NBIOT 增加指令 QIDNSCFG。
	* NBIOT 指令采用可配置型结构。
* 2019-09-22 :
	* 去除QMCData数据包的发送。
* 2019-09-18 :
	* QMCData包采用Info包结构体就好了，没必要创建一个一样的。
	* MqttSN固件旧数据组包方式遗留的去除。
* 2019-09-13 :
	* OneNET监听器加入，监听信号检出。
	* OneNET运行时间获取。
* 2019-09-11 :
	* OneNET发送数据ACKID采用自增方式，废弃原先255不变。
	* OneNET发送数据携带raiMode标志0x400方式。
	* OneNET生命周期更新包发送采用有应答方式。
* 2019-09-09 :
	* TMoteInfo上传IMSI号。
	* Radio下发workinfo去掉打印nbruntime。
	* Radio下发workinfo去掉打印apn。
	* Radio下发netinfo打印imsi。
	* mqttsn下发命令去掉:uplimit,nblimit。
	* 联通band表改为b8，b3。
	* OneNET修复bug，命令下行应答参数少一个。
* 2019-09-09 :
	* 版本号修改为149。
* 2019-09-03 :
	* 增加BM1422地磁驱动。
* 2019-09-02 :
	* 避免重启后一直无车时有个扰动就报告车辆离场。
* 2019-08-31 :
	* 为了降低对水银开关品质的依赖,增加一种激活方式:正放30秒后激活。
* 2019-08-31 :
	* 版本号修改为148。
* 2019-08-13 ：
	* NB心跳包间隔刻度改为15分钟，默认4小时(240分钟)发送一包心跳包，命令设置<在原命令基础上修改为: 命令值(1~9)为小时刻度，命令值(11~255)为15分钟刻度，【具体为设命令值为X，1<=X<=9: X小时，11<=X<=255: ((X-10)*15)分钟】>。
	* 升级固件或降级改变版本号将心跳时间改为默认时间。
* 2019-08-05 :
	* 增加当设备启动次数超过30次将不再进行测试点测试，测试点按下将无法进入测试模式。
	* 如果仍需测试点测试，可通过配置器发送命令“restore”恢复出厂参数，则仍有30次启动测试点测试机会。
* 2019-08-01 :
	* 修复因处理器或硬件差异性导致SPIFLASH在备份固件时间不同导致备份时间超时看门狗重启设备。
* 2019-07-30 :
	* 为修复MqttSN固件中DynamicInfo包有可能过长导致数据发不出来的隐患，DynamicInfo中Rvcc字段移动到BasicInfo中。
	* 增加对NBIoTV120模组的支持。
* 2019-07-25 :
	* 版本号修改为147。
* 2019-07-24 :
	* 发布146固件。
* 2019-07-20 :
	* 增加基站时间获取检查，当基站时间与设备时间偏差20min以上，将重启模组重新获取，第二次获取时间将写入，设备刚上电不用检查基站时间，当运行一天以上才检查。
* 2019-07-18 :
	* 去除“cgdcontPDPType”，“cgdcontAPN”参数的获取，这两个参数是旧版本模组中获取APN指令，目前模组已不再使用。
* 2019-07-18 :
	* 版本号修改为146。
* 2019-07-09 :
	* 发布V145固件。
	* TMoteInfo包进行字段聚合: Rlib Algo Nbboot Nbsent Nbheart Cgain Rgain。
	* TMoteInfo包新字段: Nbrun: (Nbboot Nbsent Nbrecv Nblimit Nbheart)。
	* TMoteInfo包新字段: Gain : (Cgain Rgain)。
	* TMoteInfo包新字段: RAlib: (Rlib Algo)。
	* TMoteInfo包上报HardwareVersion中去掉多余-NB。
* 2019-06-21 :
	* 版本号修改为145。
	* 单次5分钟内未注网成功也清除频点。
* 2019-06-20 :
	* 发布V144固件。
* 2019-06-18 :
	* 检测算法库更新至: 版本35: 最多记录5个历史磁场背景,每个磁场背景间隔24小时以上,以应对无车判定为有车的情况。
* 2019-06-14 :
	* EEPROM中SN号为空检查FLASH最后4字节，不为空将SN写入EEPROM。
* 2019-06-10 :
	* 版本号修改为144。
	* 单band入网时间为180秒，多band入网时间为500秒。
* 2019-05-25 :
	* 版本号修改为143。
	* WorkInfo上报运营商卡APN信息。
	* WorkInfo去除上报BeepOff信息。
	* workinfo小无线输出APN信息。
	* 增加NBIOT清除小区频点COAP,ONENET,MQTTSN同时增加。
	* 设备上电或硬件重启不清除小区频点，当多次入网不成功时开启清频(3次)。
* 2019-05-15 :
	* 测试架相关代码暂未开启。
	* 增加固件检查NBIOT模组频段是否在支持范围，当按下测试点，如未读取到IMEI或频段不匹配将警告。
* 2019-05-11 :
	* 选项配置是否在自检结束后擦除flash最后4字节数据。
* 2019-05-10 :
	* 版本号修改为142。
	* 增加测试架自检测试代码，可选开启。
	* 测试架测试当60秒后，自检未成功也发送数据。
	* 修复bug:自检数据未上报sn。
	* RF4438当收到配置器数据才上报ID。
* 2019-04-01 :
	* 版本号修改为141。
	* radar_vcc 判断阈值由28修改为27。
	* 修复因雷达供电引脚未初始化就进行雷达初始化BUG。
* 2019-03-20 :
	* 版本号修改为140。
	* radar_vcc 判断阈值由26修改为28。
	* 设备启动打印信息中增加Radar:%d, Device Reboot:%d Cause:%d Radar:%d Nor:%s, 显示radar_vcc值。
	* 修复RadarHighPass设为默认值后为写入EEPROM导致下次读取任为原值BUG。
* 2019-02-15 :
	* 解决高通滤波器判断中的一个小bug。
* 2019-02-01 :
	* 有配置器在附近的时候可以翻转初始化。
* 2019-01-29 :
	* 版本号修改为139。
	* TCFG_EEPROM_CheckNewSNorBrand()中检测新烧写设备将备份域设备号与厂牌名为空则返回true。
	* 读取磁场时,间隔5ms读取出来的差如果不大于900就认为正常。
	* 下行命令如果不存在,那么返回102。
	* MQTTSN协议固件开启小无线下发nbheart。
	* 小无线命令下发异常提示。
* 2019-01-19 :
	* 发布V138固件。
* 2019-01-19 :
	* 版本号修改为138。
	* 修复设备固件初次烧写完成，在一天内将设备倒置休眠，一天后翻转激活将会重启一次。
	* MQTTSN协议固件开启小无线下发netinfo,打印imei和iccid。
	* MQTTSN协议固件去除小无线下发指令restore恢复出厂设置。
	* MQTTSN协议固件去除小无线下发指令carindelay配置检测到有车延时多久发送数据。
* 2019-01-15 :
	* 发布V137固件。
* 2019-01-14 :
	* 解决地磁差值超过65535后变很小的bug。
	* 算法版本33: 如果磁场和雷达都波动了,磁场有车,雷达测得距离>20,即使雷达差值很小,也认为有车。
	* 版本34: 覆水时( < 12 )磁场的灵敏度可调无车的门槛一般是700~900,有车的门槛是980~1260。
	* 修复变量vptat_is_ground错误的设为无符号值的问题。
	* 1. 算法库更新到34版本,覆水时可以通过设置灵敏度来降低无车判别为有车的概率。
	* 2. 手动初始化后,将磁场保存在setmag生效的eeprom区域,避免被自动学习覆盖。
	* 近场初始化后磁场(maginit)后会保留在eeprom中,且不会被自学习覆盖。
* 2019-01-10 :
	* 远程命令下发TCLD110S,第5个字节设为msgid,随应答包中携带msgid发出。
	* MqttSN去掉radio配置nblimit，uplimit。
* 2019-01-07 :
	* RTC校准设置。
	* HAL_RTCEx_SetSmoothCalib(&RTC_Handler, 0, 0, RTC_CALR_CALM_8|RTC_CALR_CALM_7|RTC_CALR_CALM_5);
* 2019-01-07 :
	* 版本号修改为137。
* 2019-01-02 :
	* 发布V136固件。
* 2018-12-29 :
	* 间隔24小时查询spiflash备份域是否备份当前app,无备份则备份当前app。
* 2018-12-24 :
	* 发现部分设备初始化的时候背景值变小,疑似模块型号判断时出错。
	* 只在上电时判断一次模块型号,如果是主流型号就不再二次判断,如果是早期型号,那么每次测量时再判断下。
	* 重新调整了雷达模块判断逻辑,前五次测量中,如果大多数情况是0v,那么认为是带运放的模块,反之则是不带运放的模块。
* 2018-12-22 :
	* 雷达库更新到52版本,计算背景时也进行四舍五入。
	* 修改nb一天可发送数据包在7点补充到200包。
	* 修改读取NB固件版本匹配字段为APPLICATION。
* 2018-12-21 :
	* 限制NB发送包数,默认一天200包。
	* DynamicInto中 : Nblimit : 197 为当天剩余可发送包数。
	* 无线下发命令 : nblimit:200 配置一天可发送包数。
	* 远程下发命令 : TCLD110S{(NBLimit):{(val):220,(Magic):9}} 配置一天可发送包数。
	* 翻转设备可清空一天统计计数。
	* MqttSN固件由于Flash空间不足,去掉远程命令:1.传感器灵敏度。
	* MqttSN固件由于Flash空间不足,去掉无线命令:1.CDP核心网地址配置.2.COAP RA时间配置.3.蜂鸣器开关配置.
	* 优化底层hal库中检测传递形参是否为空指针的无用代码,减少Flash占用。
* 2018-12-20 :
	* 优化NB发送接收包数统计。
* 2018-12-20 :
	* 默认采样周期从10ms改回18ms。
	* 雷达库更新到51版本。
	* 当雷达芯片电压为2.5v时:默认CoverGain=7,RadarGain=13,highpass=800Hz。
	* 当雷达芯片电压为3.0v时:默认CoverGain=10,RadarGain=15,highpass=1200Hz。
* 2018-12-20 :
	* 版本号修改为136。
* 2018-12-18 :
	* 发布V135版本固件。
* 2018-12-17 :
	* 命令控制是否开启翻转初始化,默认关闭。
	* 下行指令宏控制整理。
	* CoAP发送Fifo增加到3072字节,接收Fifo增加到2048字节。
	* PCP接收Fifo增加到2048字节。
	* MqttSN固件由于Flash空间不足,去掉远程命令:1.小无线心跳间隔时间配置.2.蜂鸣器开关配置.3.RadarGain配置。
* 2018-12-15 :
	* 优化NetFifo内存大小的设置。
* 2018-12-14 :
	* 增加下行命令CfgRadar,用来配置高通滤波器,采样价格和调制电压。
	* TCLD110S{(CfgRadar):{(interval):4,(hpass):3,(tune):15,(Magic):9}}。
	* 雷达库也进行了适配,此前的49版本不完整。
	* 采样间隔默认从13改为4,雷达耗电可以降低至少1/2。
	* 同时下沙项目的老雷达供电方案采样间隔仍旧为13。
	* 去掉远程RadarGain命令。
	* 移动版去掉配置器发送workinfo,netinfo,devinfo,upgradeinfo命令。
	* 移动版去掉调试信息中携带的NB错误码。
* 2018-12-14 :
	* 优化各个Message的内存占用,采用不限定包长Fifo存储。
	* 远程升级限制信噪比降低至-80。
	* 去掉Info包中Rssi与Snr字段。
	* Info包最大上传字节修改为450字节。
* 2018-12-13 :
	* 更新算法库到32版本,可以手动设定多组磁场背景。
	* 增加的nb命令为:TCLD110S{(SetMag):{(x):[-49,0,0,0,0],(y):[-626,0,0,0,0],(z):[-530,0,0,0,0],(Magic):9}}。
	* 不增加rf命令,因为命令太长了。
	* 优化Net数据包创建相同代码Flash占用。
* 2018-12-12 :
	* Workinfo包中增加RadioRv字段,1:附近有配置器且收到配置器下发数据,0:附近无配置器或没收到配置器下发数据。
* 2018-12-11 :
	* 修改SPIFLASH读取deviceid方式，兼容XTX型号。
* 2018-12-10 :
	* 远程升级限制信噪比降低至-50。
	* 算法库更新到版本31: 增加检测模式,双传感器模式,纯雷达模式,单地磁模式. 实际只生效单地磁模式和双传感器模式。
	* 远程检测模式配置指令 : TCLD110S{(SensorMode):{(val):0,(Magic):9}} 0,1,2。
	* 小无线检测模式配置指令 : sensormode:0 0,1,2。
* 2018-12-08 :
	* 算法库更新到30版本: 当magdif值降低到300以下,同时还是积水状态,那么也判定为无车。
	* 雷达版本改为48: 覆盖增益影响方范围从频点2 3 4 5 改为 2 3 4。
* 2018-12-07 :
	* 版本号修改为135。
	* 增加测试点超时5分钟后由测试模式变为工作模式。
* 2018-12-06 :
	* 发布V134版本固件。
* 2018-12-05 :
	* 修改各个中断线中断优先级:
	* Usart1 : 1, 0。
	* Usart2 : 1, 1。
	* RF_IRQ : 1, 2。
	* TIM2   : 2, 0。
	* WKUP   : 3, 0。
* 2018-12-05 :
	* LowPowerEnterStop函数中在关闭系统嘀嗒定时器前屏蔽全部中断,在开启系统嘀嗒定时器后开启全部中断。
	* Wakeup配置放到屏蔽中断外。
	* Radio_Rf_ISR中断处理函数中,增加Radio_Rf_is_Sleep()小无线休眠判断。
* 2018-12-03 :
	* 增加宏定义选择RTC的时钟源LSI或LSE,默认LSE。
* 2018-12-03 :
	* 雷达库更新到版本29 : 当magdif值降低到150以下,同时还是积水状态,那么即使磁场没波动也判定为无车。
	* 更新了雷达库到47和算法库到29。
	* 优化解决徐州积水后,无车判定为有车的问题。
	* nb下行命令:TCLD110S{(RadarGain):{(val):12,(Magic):9}。
	* rf下发命令:radargain:12。
	* 推荐值 12~15. 值越小,增益越小,覆水影响越弱.默认值由原先的15改为12。
* 2018-12-03 :
	* 当调整覆水增益后,雷达背景也同步调整。
	* 通过小无线配置覆盖增益时,也调整雷达背景。
	* 背景调整时进行四舍五入处理。
	* 雷达 : 版本45,覆盖增益在频点2 3 4 5都进行作用,高增益:x1.25,中等增益x1,低增益x0.8。
	* 雷达库更新到46版本。
* 2018-11-25 :
	* 版本号修改为134。
	* 雷达库版本升级到43版本 增加了覆水增益调节功能。
	* 1表示增益最大,3表示增益最小,默认增益为2。
	* 1位先前版本的默认增益,覆水太敏感。
	* info中上报Cgain作为覆盖增益指示。
* 2018-11-24 :
	* 发布V133版本固件。
* 2018-11-24 :
	* DNS解析成功先设置MqttSN服务器再进行EEPROM比较。
	* PCP升级调试信息在Normal模式下也输出信息。
* 2018-11-23 :
	* 版本号修改为133。
	* 首次烧写版本升级将默认MqttSN服务器地址写入EEPROM。
	* DNS解析异常，使用EEPROM中保存的MqttSN地址。
	* DNS解析成功，比较EEPROM中保存的MqttSN地址值，不同写入EEPROM。
* 2018-11-22 :
	* 发布V132版本固件。
* 2018-11-22 :
	* 去掉Radio_Rf_TxOverISR函数中Radio_StartRX(RF_CHANNEL1, 0)。
* 2018-11-21 :
	* 远程命令"{(UpLimit):{%hd,%hd,(Magic):%hu}}" 改为 "{(UpLimit):{(rssi):%hd,(snr):%hd,(Magic):%hu}}"。
	* 地磁限定值拉大到200。
	* 关闭优化NB各个指令的执行时间（影响下行命令接收，升级异常！！！！！）。
* 2018-11-20 :
	* DNS处理优化各项执行的成功失败代码，合并同代码精简Flash。
	* 增加Other运营商模式，并配置为BAND3, BAND5, BAND20。
	* RADIO_CTS_TIMEOUT宏由2000改为200。
	* Radio_Comm_SendCmd函数中count有6改为3。
	* 优化DNS解析方式，采用上电解析+间隔1天解析+设备激活解析。
* 2018-11-19 :
	* Radio 发送读取SPI函数count=10改为count=6。
	* 优化NB各个指令的执行时间。
* 2018-11-16 :
	* MqttSN发送DisConnect指令控制优化。
	* 增加激活命令下发上报WorkInfo。
* 2018-11-15 :
	* NB硬件重启断电时间由2秒增加到3秒。
	* NB串口通信的接收中断控制去除。
* 2018-11-13 :
	* PCP升级任务启动时上报WorkInfo。
	* 统计PCP升级任务启动次数。
	* WorkInfo 增加字段 PCP:1.188-219.500.V20.130。
	* 1   : 升级任务启动次数。
	* 188 : 已获取包。
	* 219 : 总获取包。
	* 500 : 分片字节大小。
	* V20.130 : 升级版本号。
	* 升级限制SNR降低至-30。
* 2018-11-12 :
	* 版本号修改为132。
	* 增加NB间隔一周上报一包BasicInfo。
	* CoAP PCP升级 去掉每次发送数据之前检查注网。
* 2018-11-03 :
	* 增加软件重启方式的记录。
	* 并上报到平台Boot:%d.%d.%d。
	* 休眠之前关闭小无线中断Radio_Rf_Interrupt_Deinit()。
	* 配置文件移动MqttSN的DNS选择是否开启。
	* 去掉COAP每次发送数据之前检查注网。
* 2018-11-02 :
	* NB硬件重启错误超过限定次数2次,对NB串口初始化。
	* radar err信息改为warn。
	* rollingover信息等级修改。
	* EEPROM写入校验，最大5次。
	* RADIO_CTS_TIMEOUT 最大时间 10000 改为 2000。
	* PCP升级调试信息等级降低至LV2。
* 2018-11-01 :
	* 版本号修改为131。
	* MqttSN 最大订阅消息主题由5减为2。
	* HAL_UART_Transmit 超时时间由0xFFFF减为0x07FF。
	* 栈大小由0x600增加到0x800。
	* 去除MqttSN协议等待应答信息，小无线打印。
* 2018-10-23 :
	* 发布V130版本固件。
* 2018-10-23 :
	* 雷达库更新至版本42。
		* 版本42,由于峰值频率可能会摇摆,所以对距离进行校准,取两个峰值距离的中间值。
	* 检测算法库更新至版本28。
		* 版本27: 当区别无车时的细分场景,积水下的无车抑或普通无车。
		* 版本28: 距离12及以下都认为疑似积水。
* 2018-10-22 :
	* OneNET增加Write函数。
* 2018-10-20 :
	* Band模式增加多频段配置。
* 2018-10-18 :
	* OneNET实现注册上报资源列表。
* 2018-10-17 :
	* OneNET各个数据包创建兼容CoAP方式。
	* WorkInfo中CellID，采用Tac+Ci 十六进制方式上报。
* 2018-10-16 :
	* 20V130 :
	* 版本号修改20V130。
	* 选择编译Net Hander，精简SRam。
	* 增加OneNET数据包写入。
* 2018-10-12 :
	* SPIFlash 读取型号ID有点问题，改为读取设备ID。
	* 增加NB硬件重启异常连续超过5次，重启设备。
* 2018-10-11 :
	* 更换了雷达库,便于区分覆水场景还是普通场景下切换到了无车状态。--by Bindaz
	* 修复Radio下发命令不同设备号蜂鸣器也叫。
	* 增加SPIFlashID读取次数。
* 2018-10-09 :
	* 增加MqttSN等待应答消息调试打印。
* 2018-10-08 :
	* 20V129 :
	* 版本号修改20V129。
	* 增加当固件升级或更替时，CDP服务器地址重设，方便之后联通与电信设备固件更替时修改CDP地址。
	* 精简无用RadarDbg调试信息上报代码。
* 2018-10-07 :
	* MqttSN PCP 升级限制Uplimit:rsst,snr指令加入MqttSN下行指令中。
* 2018-09-30 :
	* MqttSN PCP 升级初步测试成功。
* 2018-09-29 :
	* 20V128 :
	* 版本号修改20V128。
	* 上报NB核心网和PDPType。
	* MqttSN PCP 升级初步构建完成。
* 2018-09-28 :
	* MqttSN PCP的需求，精简MqttSN协议Flash，公用相同相似代码。
* 2018-09-26 :
	* MqttSN处理接收PCP下行指令。
	* Pingreq 与 Active 的工作时间采用独立的计时器。
* 2018-09-25 :
	* NBIOT SNR 设定上下限 127 ~ -127。
	* 去掉 nbruntimeday 相关代码。
	* MqttSN PCP协议基础框架构建完成，链路层开始建立。
* 2018-09-21 :
	* MqttSN PCP协议文件结构创建。
* 2018-09-20 :
	* OneNET各个指令加入完成。
* 2018-09-19 :
	* 增加发送QmcData数据包到服务器。
	* 修改MqttSN的pingreq包发送机制，sleep时间修改为8小时。
* 2018-09-18 :
	* 20V127 :
	* 版本号修改20V127。
	* 修复126中优化队列的读写bug。
* 2018-09-17 :
	* MqttSN下行应答修改103不用返回。
	* MqttSN增加Connect与Ping调试信息。
* 2018-09-15 :
	* 优化监听器代码。
	* 去掉原先控制发送RadarInfo控制代码。
	* 修复当MQTTSN输出发送失败就要DNS解析，而不是只解析一次。
* 2018-09-14 :
	* 20V126 :
	* 版本号修改20V126。
	* 增加MqttSN监听处理，监听进入休眠时15秒后检出NB网络信息。
	* MqttSN协议增加NB运行时间统计，兼容Coap方式。
	* DNS解析可配置解析域名个数，可选MqttSN域名，去掉解析movebroad.cn，只解析mqtt.movebroad.cn。
* 2018-09-13 :
	* 20V125 :
	* 版本号修改20V125。
	* 增加MqttSN发送数据采用与Coap相同字节流数据方式。
	* 增加MqttSN错误码输出。
* 2018-09-12 :
	* 增加设备在正放休眠状态下通过平台发送指令激活设备，命令接收继续工作20秒，最大工作120秒，最大命令生效时间24小时。
* 2018-09-11 :
	* 20V124 :
	* 版本号修改20V124。
	* 对NB应答数据有可能出现前导'\0'的情况去除前导'\0'。
* 2018-09-10 :
	* 修改原根据NB注网成功则上位机联网reg，为当数据发送成功联网reg。
	* 去掉nbiotfunc.c中设置CDP服务器函数中多写的一条指令NBStatus = pClient->ATCmdStack->Write(pClient->ATCmdStack);。
* 2018-09-09 :
	* 去掉翻转控制ModulePower开断。
* 2018-09-07 :
	* 20V123 :
	* 去掉监听NB是否进入Idle模式，选着由宏配置是否开启该功能。
	* SN未写入默认为1。
	* 修改上电检查spiflash中是否有备份app为升级任务开启前备份。
* 2018-09-06 :
	* 20V122 :
	* 自动根据NB模组型号选择不同AT指令处理，可兼容利尔达，移远模组。
	* 限制SNR范围-127~127之间。
	* 修复因小无线晶振异常导致程序卡死，反复重启。
* 2018-09-05 :
	* 20V121 :
	* 调整无源蜂鸣器频率。
	* 增加上电拉低PB9，使QMC加热电阻不导通。
	* 增加对GD25Q40B SPI FLASH的支持。
* 2018-09-04 :
	* 20V120 :
	* 上报信息中，硬件型号：STM32L151xBA-...
	* 重启码兼容之前版本。
	* 增加小无线发送地磁与雷达背景值。
	* OneNET初期处理架构。
* 2018-08-27 :
	* 20V118 :
	* 增加上报NB模组厂牌和型号。
	* 修改Info信息上报,当NB联网成功后才生成Info信息包。
	* Band已频率选择。
* 2018-08-25 :
	* 20V117 : 
	* 修复获取NB工作时间计算方式错误导致多计算了1~2小时工作时间。
	* 征集BC35模组的选择。
* 2018-08-14 :
	* 增加关闭蜂鸣器的命令。
	* 解决debugval一直为0的错误。
	* 磁场dif>100 distance>10就认为有车。
	* 雷达库更新到27版本,解决雷达不动,磁场漂移到无车时,误判为无车的错误。
	* 磁场值波动很大,但是雷达波动值小于8,那么认为无车。
	* 当雷达和磁场都波动,同时当距离>16时,不管磁场如何都认为有车。
	* 即使4438挂掉,也能正常运行。
* 2018-08-10 :
	* PCP升级协议初步完成。
* 2018-07-18 :
	* status上传的雷达信息从谱线2开始。
* 2018-07-17 :
	* 默认NB心跳时间为4小时。
	* 心跳间隔默认4小时,可以1~12小时进行设置。
	* 心跳包中增加一位标记是否成功发送到了平台uint8_t nbstate:1;0=sending,1=sent。
	* 将miso引脚在休眠时设置为没有上下拉输入模式,功耗最低。
	* 在休眠前先发一个数据包,才能进入20ua以下。
	* z轴不再输出error信息。
	* 触发后过几秒才记录雷达信息,PB5拉低后会强制关掉nb。
	* 通过休眠时SCLK引脚设定为低电平输入解决低功耗问题。
	* 在状态包里带上雷达调试信息。
	* 雷达库更新到40版本,dif值在12以上,峰值频点的dif值在5以上的话就计算出距离。
	* 如果10个心跳周期都没有收到配置器的应答包,那么进入normal模式,不再发送无线调试信息。
	* 当发现配置器在附近时,心跳间隔改为5秒。
* 2018-07-13 :
	* error值变更下,解决雷达diff从17 渐变 到0时,一直保持在occupy状态的bug。
	* 磁场不动的时候的error值小改了一下。
	* 读取时间会锁定日期,因此读取时间时必须同时读取日期。
	* 去掉编译时间,增加雷达类型的上传。
	* rardar调试信息中增加qmc的温度。
* 2018-07-07 :
	* COAP增加RF输出AT指令执行错误码显示。
	* COAP数据发送检测数据是否送达时间增加至60秒。
* 2018-07-06 :
	* COAP工作时间统计采用变量存储，一天写入EEPROM一次。
	* 增加2个指令，CMEE和查看TUP信息。
* 2018-07-05 :
	* 时间获取BUG修复。
* 2018-07-04 :
	* 雷达vptat电压低于0.1v就认为前端集成运放,反之则不集成运放。
	* 当调整温漂系数时,背景值也要根据温度进行调整,那么也就是要记录背景值的温度。
	* 增加了磁场值的温漂系数,用以矫正温度带来的影响
	* rf 指令:coef:xx,xx,xx
	* nb 指令:{(MagCoef):{(x):xx,(y):xx,(z):xx,(Magic):xx}}
* 2018-07-03 :
	* 增加nb工作时间配额管理，当时间超过一天配额的一半时,除了状态包和心跳包.其他包就不发。
	* nb工作时间 超过一天配额的 2/3 时,就心跳包的间隔也强制改为4小时。
	* 配额时间可配。
* 2018-07-02 :
	* 增加COAP发送数据后检出信号值与信噪比。
* 2018-06-28 :
	* 增加NB对COAP处理时间的统计，ConnectTime和IdleTime，通过workinfo发送，nb工作时间.nb休眠时间。
* 2018-06-27 :
	* 更新了雷达库,纠正谱线2和3的背景值计算有偏差的错误。
* 2018-06-23 :
	* Bootloader改为0V20，适配该Bootloader，Bootloader减少6Kflash，NB上传INFO数据增加Boot版本号。
	* TCFG_MAG_FREQ_OFFSET 改为 TCFG_BOOT_VERSION_OFFSET。
* 2018-06-21 :
	* COAP发送数据可选则RAIDLE或NORMAL模式，在platform.h中由宏定义选择模式。
	* RAIDLE模式 : 发送数据采用RA指令发送。
	* NORMAL模式 : 普通COAP发送模式。
* 2018-06-15 :
	* Coap协议CDP服务器可通过RF或NB命令配置。
* 2018-06-14 :
	* RF输出调试信息采用等级输出，分为4个Level，Level3:输出所有调试信息,Level2不输出Radar调试信息,Leverl1不输出NB调试信息。
	* RF配置Level指令: rfdplv:3。
* 2018-06-14 : (同步更新)
	* 当雷达背景不好的时候,或者雷达无信号的时候，小无线会输出错误信息。
	* 当收到命令后,会持续3分钟,每秒都发心跳包。
	* 开启了小区重选功能。
	* 当雷达距离大于8,并且dif值大于40时就认为有车。
	* 这个可能下雪下雨有风险。
	* 增加rf命令和nb命令数上报功能。
	* 初始化雷达后,上传radardbg包。
	* 每次跳变到无车后,过一分钟就上报一个radardbg信息,这样会增加功耗。
	* 当雷达波动后,就1分钟后上报雷达信息。
	* 
* 2018-06-11 :
	* NBIOT增加监听处理器。
	* NBIOT监听35秒是否进入IDLE，没进入发送WorkInfo包，包中nbworkinfo：1Connected,0Idle。
* 2018-06-06 : 
	* 增加COAP数据下行命令执行
	* 增加COAP与MQTTSN对下行数据应答ResponseInfo
* 2018-06-02 : 
	* 增加NUESTATS=RADIO信息获取，优化上报workinfo中的频点与CellID值。
	* 增加RF输出WorkInfo信息。
	* 初始化的时候不再开关雷达。
	* 雷达波动一分钟后不再上报雷达信息。
	* soft增加BootLoader的版本号,TCFG_MAG_FREQ_OFFSET用来存储boot的版本号。
* 2018-05-26 : 
	* NB增加清空频点指令,获取当前PSM状态指令。
* 2018-05-24 : 
	* V66版本：增加NB软件版本号获取，基站信息获取。
	* info信息包中增加NB软件版本号，基站信息。
* 2018-05-23 : 
	* 1.238  为了解决磁场dif小时,有车漂移到无车,从而错误的判断为无车的bug,
	* 当偏移到无车并且dif不小于150时,如果当前dif值和3分钟前的dif值差异在1000内,并且当前不是覆盖状态,那么不改变状态。
	* 1.237  车辆驶入后,要等磁场稳定8秒或者以上才进行上报.
	* 车辆驶出后,不需要等磁场稳定8秒或者以上就可以上报.
	* 用以过滤快进快出,但不影响快出快进.
	* 增加了 {(InDelay):{(val):%hu,(Magic):%hu}} 命令
* 2018-05-21 ： 
	* 1.236  有车变到无车后,输出雷达信息。
	* 修复翻转初始化的时间需要等待很久。
	* 修复在开始翻转等待时间较久。
	* 解决：设备翻转蜂鸣器叫开始30秒内NB不工作。
* 2018-05-20 : 
	* 1.235  纠正rf信道上报错误的问题。
	* 1.234 tmoteinfo里增加cellid,可以协助检查信号质量,设备定位。
* 2018-05-19 : 
	* 1.232 状态改变的前提必须是磁场有变动。
	* 1.233 增加maginit指令,用于进行磁场初始化.还是取消状态改变必须磁场改变这个前提,雨天效果也还可以。
* 2018-05-18 :
	* DNS域名解析完成，服务器为114.114.114.114:53,解析mqttSN域名为"movebroad.cn"。
* 2018-05-17 ：
	* 修复MqttSN在停止模式时处理bug，停止模式时对其他mqttSN数据包的支持。
	* DNS初步与NB连接。
* 2018-05-16 : 
	* MQTTSN与COAP协议稳定，待增加下行处理，DNS解析开始架构
	* DNS解析应用层开始架构，DNS解析库已完成
* 2018-03-22 : 
	* MqttSN->消息缓存处理逻辑完成
* 2018-03-22 : 
	* MqttSN->初步架构完成
* 2018-03-21 : 	
	* Coap->增加停止模式下到达半小时,退出停止模式,进行数据发送处理,或有新数据需要发送时,退出停止模式

* 2018-5-11 :
	* 1.230 当雷达dif值小于5的时候,就强制判定为无车.
* 2018-5-9 :
	* 1.229 当雷达两分钟内没有波动,那么再次进行雷达检测需要间隔1分钟,这样就会引入新的bug:当旁边车位驶入触发了雷达,但是本车位紧接着有车驶入了,那么雷	* 达就不会被触发,就会导致漏车了.
	*       解决:如果这个地方半小时内磁场触发了30x4=120次,
	
* 2018-5-6 :
	* 1.227 当磁场波动,但是发现雷达最近2分钟没有波动,那么雷达的检测时间间隔要1分钟. 
	* 1.228 纠正1.227引入的积水覆盖时不准的bug,不在等待磁场稳定再上传数据,而是延后8秒就开始传数据.
* 2018-5-5 :
	* 1.226 雷达无车而且dif值为5以下,并且最近两次雷达都为无车.
	* 	  问题: 假设雷达dif值为12,
	* 	  TODO:磁场波动的情况下,设备上停了辆共享单车,就容易出现一会儿有车,一会儿无车的情况,针对这个现象只有启用地铁模式,要连续30秒有车,才认为有车
	* 	  当连续5次波动后,把旧的40个磁场dif值覆盖掉,保留最新的20个,解决全覆盖时出现漏测的问题.
	  
* 2018-5-2 :
	* 1.225 雷达无波动时才会进行磁场背景矫正

* 2018-4-30 :
	* 1.223 更新了雷达库,雷达的检测距离可以设置为0.5米到1.6米,可以通过小无线和coap进行设置.
	* 	  TODO:检测范围越大,误差也越大.1.1米变动到1.6米时,误差应该增大两倍
	* 1.224 背景设置扩展为16个频点,检测距离可到1.6米

* 2018-4-26 :
	* 1.219 解决强磁场时波动计算错误的bug
	* 1.220 bug1:未解决 数据缓存有7个buffer,但是只利用了其中的6个buffer
	* 	  bug2:解决 数据在发送成功后读取rssi值,如果读取失败就反复尝试读取
	* 1.222 当雷达dif值<4时,同时上次雷达也为无车那么就输出为无车.

* 2018-4-25 :
	* 1.218  当磁场和雷达都波动后,就将磁场的最小值和最大值改为当前值.避免反复进入波动处理,这时,当磁场dif在200左右,而雷达dif为有车时就会比较有问题.

* 2018-4-24 :
	* 1.217  当dif值变化小于6或者dif值变化小于 20%,那么认为没有变化.
	*        如果最近8秒内没有发送过数据,才会发送状态数据,防止刚变化到临界值时频繁上报状态.
* 2018-4-21 :
	* TODO:
	*  1.216 针对雷达没有波动的情况,需要磁场在近期有波动,而且磁场的阈值是常规情况的1.5倍.
	*        但是如果同样dif值情况下,未覆盖时的磁场dif为有车,覆盖是的地磁dif为无车,该如何判断?
	* 	   也就是 上次状态改变时记录的磁场状态的阈值应该以 覆盖时的阈值为准.或者索性记录状态改变时的dif值,而不是状态.

* 2018-4-20 :
	* 1.215 covercount 的值改为 带负数的 radardif.
* 2018-4-16 :
	* 1.213 发现有漏车现象,radardif只有6,但是magdif有2921,因此将雷达是否波动的阈值由10改为5
	* 1.214 问题:雷达波动比较小,而且车又停了一天以上,那么超时会对磁场背景进行校正.
	* 	  解决:当radardif值在10内时才进行磁场背景矫正
	* 	  TODO:RSSI值不是最小时才进行背景矫正. 如果连续10天没有车,那么当前的rssi应该就是最小的了.
	*        无车时RSSI值为27,有车时RSSI值在20左右
	* 		   31-27;29-23;31-22;
	* 		   与RSSI最高值的差越大,有车的权重越大.
	* 		   但如果期间基站改动过,导致rssi值变化了,就会引入问题.
	* 		   如果雷达不是绝对无车,那么当前RSSI值比最小值要大很多时才会进行矫正,这样的话,如果连续一段时间无车,就不会进行磁场背景矫正.
	  
* 2018-4-13 :
	* 1.211 radardbg中增加磁场背景信息
	* 1.212 修复命令下发处理时的bug
* 2018-4-12 :
	* 1.210 解决磁场背景矫正出错的问题

* 2018-4-9 :
	* 1.208 解决一个重要bug,解决后:磁场和雷达都有波动,而且当磁场有车,雷达完全无车时,就会判断为无车.
	* 1.209 直接通过命令设置磁场和雷达的背景值,而无需等待是否有车

* 2018-4-8 :
	* 1.206 active时翻转5次后初始化雷达再初始化地磁.
	* 1.207 取消雷达背景修正

* 2018-4-5 :
	* 1.205 当只有磁场变化是,那么要磁场从有车到无车时才会进行状态的改变,仅仅是疑似有车变化到无车,是不会触发状态改变的
	*        问题:下雨天,部分雨水覆盖在上面,车从车位上开过,那么雷达有抖动,而且最终状态是有车.
	* 	   解决:当距离大于8时才会判断为有车,否则当积水处理.
	   
* 2018-4-4 :
	* 1.204 当磁场有车,雷达无车但有变化,而且当前diff值和最近3分钟的最小值之间的差值在5内,才判断为无车.
	*       TODO:判断最近1分钟是否有抖动的门槛可以高一点
* 2018-4-3 :
	* 1.202 当雷达和磁场都波动过,最终雷达有车,而磁场无车,那么就认为有车.
	* 1.203 长期无车 的判断,从头尾无车,中间为有车的次数很小,改为头尾无车,中间不为无车的次数很小.
	*       也就是对长期无车判断更为严苛.
	* 	  
	* 	  bug:车开入时有车,但是慢慢的磁场漂移到了无车,那么状态就变为了无车.
	* 	  解决方法:当仅仅依靠磁场判断时,那么最近3分钟内,磁场必须波动过.
	* 	           因为问题主要出在有车误判为了无车,所以先在无车判断上进行试用.

* 2018-3-31 :
	* 1.200 如果雷达和磁场没有同时波动,但是两者的结果都是有车,那么判断为有车.
	* 1.201 磁场无波动的阈值由150改为210,雷达无波动的阈值由8改为10

* 2018-3-30 :
	* 1.198 如果雷达和磁场都波动过,最后磁场无车,那么就认为无车.
	* 1.199 当初始化后,状态要自动切换到无车状态,对五次磁场的平均值不在先相加再除以5而是先除以5再相加,避免越界

* 2018-3-29 :
	* 1.194 不在进行雷达 Vtune 电压的温度补偿,避免温度测量错误后,引起频域信号的调表.
	* 1.195 VTUNE的基准电压值由450改为250
	* 1.196 rf打印状态
	* 1.197 将判断雷达是否有波动从差值5改为 8,避免无车判断为有车

* 2018-3-28 :
	* 1.192 当无车的时候才会去对雷达背景进行温度补偿
	* 1.193 最近8秒磁场不波动,才发数据

* 2018-3-27 :
	* 1.187 增加地铁模式和普通模式两种工作模式
	* 1.188 增加nbiot心跳时间设置命令,可以设置1~4小时心跳间隔
	* 1.189 当雷达不波动时,只要雷达不是绝对无车,就以磁场为准
	* 1.190 默认普通模式而不是地铁模式
	* 1.191 要最近60次磁场有波动同时最近2分钟的雷达也有波动,才认为有波动,才进行状态判断

* 2018-3-25 :
	* 1.186 当纯地磁模式下,持续30秒有车或者无车,才会进行状态切换.

* 2018-3-24 :
	* 1.183 将radar的strenth 由原先的频域强度,改为时域diff值的平方和
	* 1.184 当雷达有变化时,如果雷达为无车,同时dif值在低点,那么输出无车
	*       当雷达无变化时,如果磁场连续60秒内有55次以上是无车的,那么认为无车.如果连续60秒内有55次以上是有车,那么认为有车
	* 1.185 当前频域和背景的差值平方和不大于30,当前频域差值平方和和36小时内最小值之间的差不大于8,才能进行初始化.剔除了时域信号的权重

* 2018-3-23 :
	* 1.179 当时域差值大于100000时就不认为绝对无车
	* 1.180 时域信号改为val-2470 后在求取差值的平方和
	* 1.181 时域信号仍旧用差值的平方和来判断变化量.
 	*      另外为了适应地跌沿线的车位,当时域变化量在10K内时,需要磁场和雷达同时有变化时才改变状态.
	* 	  而且当时域差值大于10K是,就不认为绝对无车,那么就不会进行无车初始化
	* 	  遗留问题:当温漂时引起雷达时域的变化超过10K时,从而导致无法进行磁场初始化
	* 1.182 同时输出时域差值平方和以及普通和

* 2018-3-21 :
	* 1.169 应用新的算法,如果磁场检测为free,那么车位状态我free;如果磁场检测为有车同时雷达确信无车,那么无车反之则为有车;
	*       如果磁场为疑似有车,雷达不确信无车,那么磁场又波动则认为有车,无波动则状态不改变;如果磁场有车,雷达确信无车,那么无车,雷达不确信无车,那么为	* 有车.
	* 1.170 磁场矫正时间改为5分钟,只要五分钟磁场无波动,同时雷达也稳定,那么就进行磁场初始化
	* 1.171 雷达最小差值的频域部分由原先的正差值改为 正负差值的绝对值和
	* 1.172 降低了磁场检测的灵敏度.
	* 1.173 解决覆水时的bug
	* 1.174 问题: 当磁场判断为了有车,但是雷达在绝对无车和无车之间切换,那么会出现一会儿有车,一会儿无车的情况..
	*              比如 旁边停了一辆车,雷达又出现了偏移的情况.
	*       应对措施: 磁场有车+雷达绝对无车 -> 无车,磁场有车+雷达疑似无车->状态不变,其它,有车.
	* 1.175 优化雷达平均值的计算
	* 1.176 时域的无车到疑似无车的门限提高了500.
	* 1.177 解决有时候小无线启动时检测不到的问题.
	* 1.178 算法也区分V1版和V2版雷达

* 2018-3-19 :
	* 1.168 增加时域上的差值和,将256个点分成了16个区域,每个区域的幅值均值

* 2018-3-15 :
	* 1.167 如果时区是0,那么强制改为32,雷达固件更新到了31

* 2018-3-15 :
	* 1.166 1小时发一个心跳包,而且每个心跳包的磁场信息和radar信息都是最近的.

* 2018-3-14 :
	* 1.164 针对车联邦有车检测到无车问题进行优化
	* 1.165 获取不到时间的话,就重启nb模块

* 2018-3-8 :
	* 1.163 更新雷达库到7版本,有车变化到无车的diff值必须要相差8以上,以解决雷达检测在临界值无车有车反复波动的情况
	* 	  连续600次中有590次磁场比较稳定,那么会进行地磁背景初始化,避免之前1分钟磁场稳定就初始化导致经常出现背景有误的情况


* 2018-3-7 :
	* 1.162 修正当4438出错时,经常进入终端读取4438寄存器的bug

* 2018-3-6 :
	* 1.161 水银开关翻转后到断开状态,再过100ms二次检测,依然在断开状态再进行激活和唤醒动作
* 2018-3-3 :
	* 1.159 更换雷达库到30版本,RV2版本雷达的覆盖检测灵敏度也可调.
	*       针对流量应用,建议检测灵敏度设置为最低talgo_set_sensitivity(SENSE_LOWEST-1);
	* 	  workinfo改成了字符串
	* 1.160 修改nbiotfunc中的bug,当收到应答后,没有收到预想的数据,那么返回error

* 2018-3-1 :
	* 1.156 醒着时翻转五次进入休眠,休眠时翻转五次进入醒着,醒来时会对设备进行初始化
	* 1.157 醒着时翻转五次对设备进行初始化,休眠时翻转五次进入激活态
	* 1.158 V1版也输出雷达信息

* 2018-2-28 :
	* 1.152 针对新款雷达模块,对雷达背景加入了温度微调功能
	* 1.153 解决自动进入休眠的bug
	* 1.154 雷达库更新到28,总增加的diff值要达到20才认为有车
	* 1.155 将发送数据的超时时间由20秒改为6秒,解决偶尔重启的bug

* 2018-2-24 :
	* 1.151 在测量电压时deinit radar 但不initradar,否则会导致雷达的adc启动异常,可能和dma有关.

* 2018-2-24 :
	* 1.149 更新雷达库到1.149版本,更加灵敏

* 2018-2-23 :
	* 1.146 radardbg:x
	* 1表示间隔15分钟2间隔30分钟 3间隔45分钟 4 5 6间隔90分钟
	*    初始化si4438的时候会最多尝试3次.   
	* 1.147 默认radardbg的间隔为2小时	
	* 1.148 radardbg输出两种dif,一种问增加的diff值,一种是 增加和减少累计的diff值.

* 2018-2-13 :
	* 1.144 部分nb命令一次执行最多获取3次,因为只执行一次的时候偶尔会返回error,不知道什么原因
	* 1.145 NBIOT_BUFFER_SIZE 开大到512
* 2018-2-12 :
	* 1.143 翻转后15秒才关闭nb模块
* 2018-2-10
	* 1.141 升级命令收到后,把数据写入eeprom时,最多写5次,确保写入成功
	* 1.142 TCLD110S{(Background):{(val):0,(Magic):9}}  直接可初始化车位背景

* 2018-2-9 :
	* 1.139 RadarDbg 的一些信息进行单独提取出来,0点的时候重启nb模块去对时.
	* 1.140 增加了power on reset,并在这时进行无车初始化


* 2018-2-8 :
	* 1.137 radardbg默认为开启状态
	* 1.138 为了省电改成2小时发一个调试包

* 2018-2-6 :
	* 1.136 在通过nbiot下发初始化背景命令时,可以设定radardif的中心值,当在中心值+-5时,才执行初始化命令
	*       初始化命令为 TCLD110S{(Background):{(val):25,(Magic):9}}
* 2018-2-4 :
	* 1.130 在给无线模块断电时,要将spi cs 引脚拉低,否则无法将模块电压拉到0V,并上报无线信道.
	* 1.131 bug:如果小无线一直发不出去,那么就会经常处于重启中.
	* 	  修正:当连续30次发送失败的话,就标记小无线为error
	* 1.132 考虑到eeprom可能哪里被篡改,当active的存储值为1时是未激活,其他值都为激活态.
	* 1.134 只有在重启后才进行对时
	* 1.135 每隔24小时,如果队列是满的,那么硬重启nb模块,如果队列是空的,那么软重启nb模块

* 2018-2-1 :
	* 1.126 更新雷达库到20版本
	* 1.127 当小无线连续三次发送识别就重启无线模块.
	* 1.128 当重启后,会上报状态,并带上上次事件的时间和count值
	* 1.129 状态包的status值第一位0和1表示状态,第二位0和1表示是否为心跳包.

* 2018-1-28 :
	* 1.124 coap的packet number和小无线的packet number独立开
	* 1.125 更新雷达库到18版本,支持新雷达模块

* 2018-1-27 :
	* 1.122 radardbg模式下,一个小时发一个雷达信息包
	* 1.123 更新到15版本的雷达库,当频率2的变化值占比超过总变化值的2/5时,就认为是覆盖

* 2018-1-26 :
	* 1.121 算法库更新到3,优化覆盖时有车无车频繁切换的bug

* 2018-1-24 :
	* 1.115 设备进入 not active 模式时,在心跳包的工作模式中显示出来
	* 1.116 解决sprintf换行不慎到此的小问题
	* 1.117 解决无车时radardif为0的bug
	* 1.118 解决雷达幅值低于10而判断为无车的bug
	*       导致后两分钟内仍旧能够发出数据,并且工作模式会发出来,idle模式值为4
	* 	  进入active模式后,也会通过nbiot发送workinfo消息
	* 	  进入idle模式2分钟后关闭nbiot电源时会清空nbiot的一些变量,进入active模式后启动nbiot电源时就会重新去连接.
	* 1.119 加快qmc的读写速度,每秒耗时唤醒的时间为35ms
	*       设备重启次数也记录下来.
	* 1.120 防止固件升级异常,将启动计数清零放在工作45秒后进行	  

* 2018-1-22 :
	* 1.109 由于nbiot模块波特率的支持范围在9520~9930,所以,我们把初始波特率由9600改为9700
	* 1.110 更新了算法库
	* 1.111 30秒内连续翻转5次即进行激活.非激活状态,小无线仍旧工作,主要关闭的是雷达,地磁和nbiot
	* 1.112 解决未能激活的bug
	* 1.113 把nbiot的重启次数记录下来.
	* 1.114 idle模式持续时间超过15分钟进入not actived模式
	*       睡眠模式 -> 空闲模式 -> 激活模式

* 2018-1-20 :
	* 1.104 增加启动nbiot模块时进行波特率矫正的功能	  
	* 1.105 增加了数据发送成功后,就进行时间矫正的功能
	* 1.106 温度补偿改为-20~60摄氏度
	* 1.107 RadarDbg中加入了x y z三轴信息
	* 1.108 将检测逻辑做成了单独的一个文件,并封装成类库.
	*       剔除了hal_radar.c和hal_radar.h
	  
* 2018-1-19 :
	* 1.102 增加命令设置nbiot模块手动进入standby模式的功能
	*       TCLD110S{(NBiotPSM):{(val):1,(Magic):9}}
	* 1.103 雷达的diff值超过255的时候,就修正为255.
	*       心跳包的时间不把状态时间改掉.

* 2018-1-17 :
	* 1.96 主频改为4MHz
	* 1.97 疑似解决第一包的雷达数据有问题的bug
	* 1.98 发完数据后进入接收模式需要一定的时间,所以网关收到心跳后要延迟5ms进行数据发送.
	* 1.99 减少了雷达的打印信息
	* 1.100 当雷达检测到有车,地磁检测到无车->有车->无车,那么认为有车
 	*      当车驶入的时候,一开始磁场变化大,接着磁场变化很小,同时最近24次雷达检测中不是全部都为有车状态,
	* 	  这种情况也要判定为有车
	* 1.101 温度补偿公式改为 -15~55 之间 每度改变的值由5改为6

* 2018-1-15 :
	* 1.91 更新了11版本的雷达库

* 2018-1-9 :
	* 1.68 dynamic info中带上雷达检测计数,每次雷达检测采样6个周期
	*      增加对命令TCLD110G{(Info):{}}的响应
	* 	 修复定时处理任务函数的bug
	* 1.69 上报字符串信息前先将缓存清零
	* 1.70 修正电池电压测量时错误的bug
	*      改为每小时记录一次雷达到eeprom
	* 1.71 增加了TRF_MSG_GENERAL_CMD命令,16字节的内容可以带上各种命令,"reboot"可以用来重启设备
	* 1.72 radio在si446x_reset时用delay函数.
	* 1.73 无论调试模式还是普通模式,通过nbiot发送的消息都会带上信号强度等值.
	* 1.74 启动时加入了打印信息,判断何时重启
	* 1.75 修改了调试口uart2中断,规避normal模式重启的问题
	* 1.76 存储方式改为大端模式
	* 1.77 进入休眠前将radar电源关闭
	* 1.78 更多的雷达库打印信息
	* 1.79 如果雷达的触发数据变了,那么每10分钟都上传下雷达的各种数据
	* 1.80 雷达调试信息改为 TCLD110P{"SN":"81010002","RadarDbg":"4,10,14;12,3,3;11,5,4.0.20,19.6,6,3,3.dif=18.16C"}
	*      改为每半小时上报一次雷达信息,加入温度
	* 1.81 增加设置sn的命令 newsn:%x
	* 1.82 通过ip%08x:%hu命令设置ip和端口
	* 1.83 解决设置服务器ip和端口的bug
	* 1.84 疑似解决可能导致radar开启上百次的问题
	* 1.85 cdp生产平台地址				"117.60.157.137"	
	* 1.86 设置完ip地址后,把所有nbiot的数据都清空,同时上传一个dynamicinfo消息
	* 1.87 动态信息里带上温度值,因为电压会随着温度变化
	* 1.88 通过该命令可以设置是否输出雷达调试信息.TCLD110S{(RadarDbg):{(val):1,(Magic):9}}
	* 1.89 每一小时存储一下磁场背景,重启前也存储下磁场背景,启动时从eeprom中读取磁场背景
	* 1.90 每次状态变化都把count存储到eeprom中
	* 1.92 x y z还是导出来,信号质量和雷达信息一起发出来 
	* 1.93 温度越低,vtune基准电压也越低.0~0.85V波动,可调电压为0~2.55V
	* 1.94 修改温度补偿逻辑,-15~55度之间的vtune基准电压从 100~450之间调整
	* 1.95 可以将信道设置为36或者4 channel:0 为信道36,channel:1为信道4

* 2018-1-7 :
	* 1.65 nbiot模块在发送完成后不进入standby模式
	* 1.67 收到ip后改为
* 2018-1-7 :
	* 1.64 实现了温度测量
	* 1.66 收到错误消息后,会上报basicinfo
	* 1.67 增加了地磁瞬变时的打印信息 
* 2018-1-6 :
	* 1.40 解决timeout后再也不发数据的错误
	* 1.42 每24小时检查下,如果有数据要发送,那么重启nbiot模块,避免nb模块逻辑出错.
	* 同时该版本不会将nb主动进入休眠模式
	* 1.44 发送成功后主动进入休眠模式
	* 1.46 翻转后会从新初始化nb模块和其变量,并将缓存的数据清空
	* 1.48 解决了连不上网了后 反复尝试连接的错误.
	* 1.54 解决trf_printf时,调用radio库时超时阻塞超过1秒的问题
	* 1.58 翻转的生活会哔哔哔的响几声
	* 1.60 NBIOTFeedbackErrorNumOfTimes由3改为1,也就是20~40秒还没有收到反馈,就重启模块再进行发送.
	* debug模式下status成员中x 对应的是温度,y对应的是rssi,z对应的是信噪比snr.
	* 1.62 温度测量还有问题. workmode保存在了eeprom中.
* 2018-1-4 :
	* 1.30 加入断电重启
	* 1.32 解决调试信息长包模式丢包的问题.
	* 1.31 不会进入standby模式
* 2018-1-3 :
	* 1.20 每天上报电池电压和工作模式等信息
	* 1.22 增加了下发指令的接收和处理
* 2018-1-2 :
	* 1.14 优化了coap命令发送
* 2017-12-30 :
	* 1.将各级的灵敏度阈值提高100,减少误触发
	* 2.合成coap,但是会看门狗超时重启
* 2017-12-29 :
	* 0.76 在和背景磁场进行比较时,需要连续两次以上同样状态才会记录,然后再触发雷达.避免地磁传感器的波动而误触发雷达.
* 2017-12-19 :
	* 0.34 每次触发雷达检测,并雷达检测出无车后,就去校准地磁背景值.TODO:地磁稳定30次后再将当前值作为背景,最好是见最近5次的平均值作为背景值
	* 0.35 磁场值和背景进行比较时,才能够有车跳变到无车时只记录状态,但不直接触发雷达.避免临界状态下反复触发雷达而过于耗电.
	* 0.41 增加了调试信息,trf_printf函数可以将调试信息通过小无线发出,目前一条信息不得超过32字节.
	* 0.43 有车哔哔,无车哔
	* 0.48 调试模式时会每隔10秒打印地磁信息,同时在启动雷达时也会打印雷达信息.
	* 问题:有次,在有车状态下不管地磁怎么改变,都不再打印出雷达信息了,不知何故?
	* 0.54 将采样点的间隔由10x11us改为10x12us,同时雷达开启后的等待时间改为1ms
* 2017-12-18 : 
	* 0.23 修改代码即使SI4438不焊接也可以工作
	* 0.24 水银开关断开则进入工作模式
	* 0.32 状态改变时会立刻通过小无线的心跳包进行发送
* 2017-12-17 : 
	* 增加了蜂鸣器的支持,当收到GET命令时,就会哔一声,方便定位设备.
