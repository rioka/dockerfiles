# escape=`
# note SDK does not include workload "Data storage and processing"
# so cannot build database project
FROM mcr.microsoft.com/dotnet/framework/sdk:4.8 AS build

# Install DataBuildTools
RUN curl -fSLo vs_BuildTools.exe https://download.visualstudio.microsoft.com/download/pr/5f914955-f6c7-4add-8e47-2e090bdc02fa/bc60b587587d10eacc50fe99a6f3d57a81749cb55c904225892d1d165f01a913/vs_BuildTools.exe `
    && start /w vs_BuildTools.exe ^ `
        --add Microsoft.VisualStudio.Workload.DataBuildTools ^ `
        --quiet --norestart --nocache --wait `
    && powershell -Command "if ($err = dir $Env:TEMP -Filter dd_setup_*_errors.log | where Length -gt 0 | Get-Content) { throw $err }" `
    && del vs_BuildTools.exe