# uber_server

接口1：用户首次启动app自动注册为用户

    请求时机：用户首次启动app时

    发送数据：{"uid":"xxxxxx"}

    返回数据：{"status":0,"message":"xxxx"} 0:succeed, !=0: 失败
    
    demo: 192.168.10.115:8001/user_register?json={"uid":"xxxxxx"}

接口2：设置用户资料

    请求时机：首次启动是选择个人标签，或者通过设置页面修改个人资料

    发送数据：{"uid":"[userid]","gender":"男：1，女：0","tag":"[技术，漂亮]","icon":"binary","uber_id":"xxx","uber_key":"xxxx","password":"xxxx"}, uid是必须的，其它可选

    返回数据：{"ret":"ok/error"} 失败或者超时后重新发送

    demo: 192.168.10.115:8001/user_profile?json={"uid":"[userid]","gender":"男：1，女：0","tag":"[技术，漂亮]","icon":"binary","icon":"xxx","uber_id":"xxx","uber_key":"xxxx","password":"xxxx"}

接口3：推送(拉取)标签

    推送时机：用户正乘坐uber去某个热门位置
    
    (拉取接口：{"uid":"xxx"}, 192.168.10.115:8001/event_label?json={"uid":"[userid]"})
    
    推送/返回数据：{"label_id":"中午一起吃饭","label_id":"下午玩桌游"....} 
    
    demo: 192.168.10.115:8001/event_label?json={"uid":"[userid]"
    
接口4：用户对某个标签感兴趣

    推送时机：用户点击了一个兴趣标签
    
    请求数据：{"uid":"xxx","label_id":"xxx"}
    
    返回数据：{"status":0,"message":"xxxx"} 0:succeed, !=0: 失败 
    
    demo: 192.168.10.115:8001/selected_label?json={"uid":"[userid]","label":"xxx"})


接口5：查询对某个标签感兴趣的所有用户

    推送时机：用户点击了一个兴趣标签“以后”
    
    请求数据：{"uid":"xxx"}
    
    返回数据：{"users":[{"uid":"xxx","icon":"xxx","tag":"xxx","gender":"xxx"},{"uid":"xxx","icon":"xxx","tag":"xxx","gender":"xxx"}]} 
    
    demo: 192.168.10.115:8001/same_user?json={"users":[{"uid":"xxx","icon":"xxx","tag":"xxx","gender":"xxx"},{"uid":"xxx","icon":"xxx","tag":"xxx","gender":"xxx"}]}

    
    
    
    