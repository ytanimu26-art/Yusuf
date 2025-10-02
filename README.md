import pygame
import sys

# initialize pygame
pygame.init()

# Screen settings
width, height = 500, 500
screen = pygame.display.set_mode((width, height))
pygame.display.set_caption("Simple Car Game")

# Colors
WHITE = (255, 255, 255)
RED = (200, 0, 0)

# Car settings
car_width, car_height = 50, 80
car_x = width // 2 - car_width // 2
car_y = height - car_height - 20
car_speed = 5

# Game loop
running = True
while running:
    screen.fill(WHITE)

    # Events
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            running = False

    # Key press
    keys = pygame.key.get_pressed()
    if keys[pygame.K_LEFT] and car_x > 0:
        car_x -= car_speed
    if keys[pygame.K_RIGHT] and car_x < width - car_width:
        car_x += car_speed
    if keys[pygame.K_UP] and car_y > 0:
        car_y -= car_speed
    if keys[pygame.K_DOWN] and car_y < height - car_height:
        car_y += car_speed

    # Draw car
    pygame.draw.rect(screen, RED, (car_x, car_y, car_width, car_height))

    # Update
    pygame.display.flip()
    pygame.time.Clock().tick(60)

pygame.quit()
sys.exit()# Yusuf
