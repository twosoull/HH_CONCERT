# 콘서트 티켓 대기열 시스템

이 프로젝트는 콘서트 티켓 대기열을 관리하는 시스템입니다. 대용량 트래픽을 처리하고, 효율적으로 티켓을 예매할 수 있도록 다양한 기술을 사용했습니다. 주요 기능으로는 Redis와 Kafka를 활용한 분산 처리, DB 락을 통한 동시성 관리, 그리고 토큰 방식의 대기열 관리가 포함되어 있습니다.

## 기술 스택

- **Backend Framework**: Java Spring Boot
- **Persistence Layer**: Spring JPA, H2 Database
- **Distributed Systems**: Redis, Kafka
- **Architecture**: Clean Layered Architecture
- **Testing**: Test Driven Development (TDD)

## 시스템 구성

- **대기열 관리**: 사용자는 토큰 방식을 통해 대기열에 들어갑니다. 대기열의 순서를 관리하기 위해 Redis를 활용하여 높은 성능을 보장합니다.
- **동시성 처리**: 대용량 트래픽을 처리하기 위해 DB 락과 Redis 분산락을 사용하여 동시성을 관리합니다.
- **카프카**: 이벤트 기반 처리로 시스템의 확장성과 안정성을 강화합니다.
- **트래픽 속도**: DB indexing 및 redis 서버 분산으로 속도를 높였으며, k6 부하테스트 진행

## 사용법

1. 콘서트 티켓을 예매하려면 대기열에 들어가야 합니다.
2. 대기열에 들어가면 고유한 토큰이 발급됩니다.
3. 대기열이 진행되며, 티켓 예매가 가능한 시점에 알림을 받게 됩니다.

## 테스트

이 프로젝트는 TDD(테스트 주도 개발)를 기반으로 작성되었습니다.
