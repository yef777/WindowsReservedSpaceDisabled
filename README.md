# WindowsReservedSpacedisabled
一键禁用windows10/11保留系统空间7GB
复制一下代码，保存为txt，文档另存为（编码为ANSI）后缀为bat文件，双击即可运行禁用系统保留空间。

@echo off
%1 mshta vbscript:CreateObject("Shell.Application").ShellExecute("cmd.exe","/c %~s0 ::","","runas",1)(window.close)&&exit
 
::查询系统保留空间是已启用并禁用系统保留空间释放7GB空间
DISM.exe /Online /Get-ReservedStorageState | find "已禁用" || DISM.exe /Online /Set-ReservedStorageState /State:Disabled && echo 已禁用保留空间
 
::启用系统保留空间重启系统后将重新占据7GB空间
::DISM.exe /Online /Set-ReservedStorageState /State:Enabled
 
pause
