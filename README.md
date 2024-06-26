<div align="center">

# **[ROS_DAY]** World Best Camera Project
<img src="https://img.shields.io/badge/ROS2-22314E?style=for-the-badge&logo=ros&logoColor=white">![OpenCV](https://img.shields.io/badge/opencv-%23white.svg?style=for-the-badge&logo=opencv&logoColor=white)

</div>

# **Object**
---
1. **ROS2**와 **OpenCV**를 cv_bridge 라이브러리를 통해 연동하여 **"World Best Camera"** Dev Project 진행
2. **ROS Package**를 직접 만들기 : 구독, 발행, 서비스 모두 포함
3. OpenCV 기반 카메라 구현 및 다양한 필터 기능 연동
4. **ROS Launch**를 통한 **Batch Execution**

     
# Prerequisites
---  
  
### 1. Installation - ROS2(Humble)

<table>
  <tr>
    <td><div align="center"><strong><font color="black">OS</font></strong></div></td>
    <td><div align="center"><strong><font color="black">ROS</font></strong></div></td>
  </tr>
  <tr>
    <td>Ubuntu 22.04.4 LTS</td>
    <td>Humble</td>
  </tr>
</table>  

<br>  

* How to install [ROS2](https://docs.ros.org/en/humble/Installation/Ubuntu-Install-Debians.html) **<<^^?**  
   
<br>  
                                                                                                        
### 2. Installation - OpenCV
  * Install **opencv-python**   
       
     ```
     pip3 install opencv-python
     ```

  * Install **ros-humble-cv-bridge**
      
    ```
    sudo apt install ros-humble-cv-bridge
    ```

  * Install **rqt**  
  
    ```
    sudo apt install ros-humble-rqt*
    ```

# Implement
---
 * Git Clone my Package 
   
   ```
   git clone https://github.com/dyjung-dev/ros2_camera_project.git
   ```

   
  + work space에서 빌드하기

    ```
    cd ros2_camera_project
    cd ros2_oneday
    ```
    work space 까지 들어가면 아래 이미지 처럼 ls 명령어 실행시 build, install, log, src 파일이 보여야 한다
    
        ![image](https://github.com/dyjung-dev/ros2_camera_project/assets/137265648/a97fee0b-09bd-4787-b8bf-abb698e47de2)

    colcon build를 한다
    
        ![image](https://github.com/dyjung-dev/ros2_camera_project/assets/137265648/cc6f7b8d-6394-44da-8cf5-99be7e5df4f6)



    **만약에 , colcon build를 실행 했는데 아래와 같은 에러가 발생한다면**
    
        ![image](https://github.com/dyjung-dev/ros2_camera_project/assets/137265648/d92145b6-8af9-48dd-a23c-ac94920af66e)

    에러가 발생한 ros2_oneday/build/CMakeCache.txt 파일을 찾아서 들어간다
    
        ![image](https://github.com/dyjung-dev/ros2_camera_project/assets/137265648/70396117-bb90-494a-a7ee-7ad88b0da8bc)

    변경된 경로에 맞게 CMakeCahe.txt 파일을 수정한다



      + 수정 전
   
          ![image](https://github.com/dyjung-dev/ros2_camera_project/assets/137265648/da20f844-c799-41f7-b956-1dd85e5dd77b)

          ![image](https://github.com/dyjung-dev/ros2_camera_project/assets/137265648/0b98a92f-e8b3-47be-8168-4062284d9965)

          ![image](https://github.com/dyjung-dev/ros2_camera_project/assets/137265648/ed056c14-7429-47a5-8257-d1131f6df9a8)

          ![image](https://github.com/dyjung-dev/ros2_camera_project/assets/137265648/cac5b4f3-037d-4910-8113-4ed523aa93a9)




      + 수정 후

          ![image](https://github.com/dyjung-dev/ros2_camera_project/assets/137265648/2255cfd3-cf02-4d50-b24f-b302cb3f00fd)

          ![image](https://github.com/dyjung-dev/ros2_camera_project/assets/137265648/5cc9b77b-fdca-4a65-b5b1-ef9e24721738)

          ![image](https://github.com/dyjung-dev/ros2_camera_project/assets/137265648/42bc5665-7087-42d2-be23-6e63b7b7de1e)

          ![image](https://github.com/dyjung-dev/ros2_camera_project/assets/137265648/7c8d8e56-c3c0-4063-9fb0-61b4d7187314)

        

      수정하고 나면, 아래 이미지와 같이 빌드가 성공적으로 끝난다

    

          ![image](https://github.com/dyjung-dev/ros2_camera_project/assets/137265648/2c308992-55c9-46eb-b679-ed9e250fa5ac)

    

  + source 명령어를 이용해서 실행 환경을 불러오기
   
       
   
        ![image](https://github.com/dyjung-dev/ros2_camera_project/assets/137265648/9d3eef05-86b7-45ae-9315-4992897fd629)

    

  + capture, video record 노드를 실행해보려면 저장 경로지정이 필요하다

      cap_parameters.yaml, rec_parameters.yaml 파일 안에서 경로를 수정할 수 있다
   
       
     
        ![image](https://github.com/dyjung-dev/ros2_camera_project/assets/137265648/0d9afa19-bb1f-4530-a1e1-67f1d74f378f)



      + 수정 전
   
        
        ![image](https://github.com/dyjung-dev/ros2_camera_project/assets/137265648/d1fe0d18-19be-41dd-b0a5-d3ce3580c5e4)

   

      + 수정 후
   
        ![image](https://github.com/dyjung-dev/ros2_camera_project/assets/137265648/665fc36c-66b3-48dd-92e0-deb8b3c75d50)

   

   
  + 먼저 img_publisher를 실행해보자
    
    이 노드에서는 카메라로부터 이미지를 받아온다
    

        ![image](https://github.com/dyjung-dev/ros2_camera_project/assets/137265648/f798dd94-f20a-4cc2-bc43-6b65fe5c020c)

        ![image](https://github.com/dyjung-dev/ros2_camera_project/assets/137265648/317749d9-c3bf-42a3-9ee0-b55b78e1524c)

   

    rqt를 실행하면 영상도 확인 할 수 있다
   
   
        ![image](https://github.com/dyjung-dev/ros2_camera_project/assets/137265648/1e5c50a4-52b0-4f91-b42e-15e69dad8c8c)





## ShowCase :rocket:
---

  ### Capture
  
    ![capture_demo-ezgif com-video-to-gif-converter](https://github.com/dyjung-dev/ros2_camera_project/assets/137265648/eebbbe08-a164-4183-bdb5-d5a08c4f2fbf)
