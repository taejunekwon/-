# -<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>KakaoMap Example</title>
    <style>
        #map {
            width: 350px;
            height: 350px;
            margin-bottom: 10px;
        }

        #searchInput {
            width: 250px;
            margin-right: 10px;
        }

        #searchButton {
            cursor: pointer;
        }
    </style>
</head>
<body>
    <div>
        <!-- 맵을 표시할 영역 -->
        <div id="map"></div>

        <!-- 검색 입력칸과 버튼 -->
        <input type="text" id="searchInput" placeholder="검색 위치 입력">
        <button id="searchButton" onclick="searchLocations()">검색</button>
    </div>

    <script src="https://dapi.kakao.com/v2/maps/sdk.js?appkey=204a7c5835adfe98d1f80dbb2054fab3"></script>
    <script>
        // 맵을 초기화하고 표시하는 로직 추가

        // 검색 버튼 클릭 시 실행될 함수
        function searchLocations() {
            var searchLocation = document.getElementById('searchInput').value;

            // 예시: 검색한 위치로 맵 이동
            if (searchLocation) {
                var geocoder = new kakao.maps.services.Geocoder();

                // 주소로 좌표 변환
                geocoder.addressSearch(searchLocation, function(result, status) {
                    if (status === kakao.maps.services.Status.OK) {
                        var coords = new kakao.maps.LatLng(result[0].y, result[0].x);
                        map.setCenter(coords);
                    } else {
                        alert('검색 결과가 없습니다.');
                    }
                });
            } else {
                alert('검색할 위치를 입력하세요.');
            }
        }
    </script>
</body>
</html>
